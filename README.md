# pocket2csv

A simple bash script to export your [Pocket](https://getpocket.com/) bookmarks to a CSV file.

For this script to work, you need:

* A [Pocket API Consumer Key](https://getpocket.com/developer/docs/authentication)
* Access to a web browser
* [jq](https://stedolan.github.io/jq/)
* [curl](https://curl.haxx.se/)
* [bash](https://www.gnu.org/software/bash/)

There is a [blog post](https://medium.com/netdef/export-your-pocket-bookmarks-to-csv-7e66997b9b98) to demonstrate script usage.

For a demo on how to use `pocket2csv`, see [Export Your Pocket Bookmarks to CSV](https://medium.com/netdef/export-your-pocket-bookmarks-to-csv-7e66997b9b98).

## Features

### New Flags for Consumer Key and Access Token

We have introduced two new flags to streamline the process of passing the consumer key and access token directly via the command line.

- `-k` flag: Use this flag to pass the consumer key directly.
- `-t` flag: Use this flag to pass the access token directly.

### Usage

#### Passing Consumer Key

You can now pass the consumer key directly using the `-k` flag. This will skip the prompt for user input.

```sh
./pocket2csv -k YOUR_CONSUMER_KEY
```

#### Passing Access Token

Similarly, you can pass the access token directly using the `-t` flag. This will skip the OAuth authorization step.

```sh
./pocket2csv -t YOUR_ACCESS_TOKEN
```

### Example

To use both flags together:

```sh
./pocket2csv -k YOUR_CONSUMER_KEY -t YOUR_ACCESS_TOKEN
```
