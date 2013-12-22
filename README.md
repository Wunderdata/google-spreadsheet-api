google-spreadsheet-api
======================

Implementation of the Google Spreadsheet API 3.0

[![Build Status](https://travis-ci.org/MikeRoetgers/google-spreadsheet-api.png?branch=master)](https://travis-ci.org/MikeRoetgers/google-spreadsheet-api)

## Status

This is still a WIP. Keep in mind that everything can change until 1.0.0 is reached. Currently only reading data is implemented.

## Authorization

The lib is only tested with the OAuth 2.0 authorization method.

It is your responsibility to make sure the access token is valid. The client does not refresh the token automatically.

## Basic Usage

```php
<?php

// Instantiate the Google client.
// You need a valid access key and the Buzz browser for HTTP requests.
$client = new \Wunderdata\Google\Client($accessKey, $buzz);

// Get a list of all spreadsheets
$spreadsheets = $client->loadSpreadsheets();

// Load all worksheets from the first spreadsheet in the list
$worksheets = $client->loadWorksheets($spreadsheets[0]);

// Load the cell feed for the first worksheet in the list
$cellFeed = $client->loadCellFeed($worksheets[0]);

// Get content from cell B3
$b3 = $cellFeed->findCell('B3');
```

Check out the [official documentation](https://developers.google.com/google-apps/spreadsheets/#authorizing_requests) regarding authentication.