# Letterboxd ratings exporter

Exports Letterboxd ratings into a JSON file.

## Installation

`npm install`

## Exporter usage

Open the file `letterboxd-export.js`.

Change `LETTERBOXD_USERNAME` to your username.

If you already have updated Taste.io with your ratings, force `TASTE_DEFAULT_STATUS` to `true`. If you want to force update all ratings, set it to `false`. Otherwise keep the `null` value, then the script will look at your local cache and only rate if needed.

### Start exporting

`npm run letterboxd-export`

The script will run and you should see a log of which movies & ratings that has been fetched. When completed there should be a `movies.json` in your project folder.

## Import ratings to Taste.io

Exported Letterboxd ratings could be imported into Taste.io.

## Taste.io importer usage

Open the file `taste-import.js`;

Login to taste.io and go to your home page. Open your browser's developer tools / inspector to the network tab. Refresh the page and look for the request to the `/me` endpoint. Copy the Authorization token (without the `Bearer` part) from the headers tab and paste into the `TASTE_TOKEN` variable value.

![Chrome Example](/images/taste-chrome-example.png)

### Start importing

`npm run taste-import`

The script will output `NOT FOUND: {movie title}` and `NOT RATED: {movie title}` if rating problems occur.

## Combine export and import

When you already have a `movies.json` file, and want to run the exporter, then the importer for all new ratings.

It's recommended to use `TASTE_DEFAULT_STATUS = null;` for this.

`npm start`
