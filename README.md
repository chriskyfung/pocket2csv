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

## Contributions

The following modifications were made by [Chris K.Y. Fung](https://github.com/chriskyfung):

1. **Command-Line Usability**
   - Added `-k` and `-t` flags to allow users to pass the consumer key and access token directly via the command line.
   - Introduced a `--mode` flag to support different script modes: `download`, `to_csv`, and `all`.
   - Streamlined user interactions by skipping unnecessary prompts or OAuth steps when these flags are used.

2. **Pagination and Progress Tracking**
   - Implemented pagination support to fetch bookmarks in batches of 30 items from the Pocket API.
   - Added real-time progress tracking, displaying download progress as a percentage for better user experience.

3. **JSON Processing Enhancements**
   - Improved JSON processing logic to handle null values gracefully using `select(. != null)`.
   - Optimized field conversions (e.g., `item_id`, `favorite`, `time_added`) for type consistency and error prevention.
   - Fixed tags processing to correctly extract and concatenate tag names from the Pocket API response.

4. **CSV Generation Improvements**
   - Refactored CSV generation logic to dynamically generate column titles and append data rows with proper alignment.
   - Expanded the `COLUMN_KEYS` array to include additional fields such as `status`, `time_updated`, `time_read`, `time_favorited`, `top_image_url`, `resolved_id`, `is_article`, `listen_duration_estimate`, `authors`, and `domain_metadata`.
   - Ensured robust handling of null values and compatibility with the Pocket API's complete data structure.

5. **General Usability and Performance**
   - Reduced redundant prompts and improved error handling for a smoother user experience.
   - Refactored authentication flow and Pocket API data handling for improved clarity and modularity.
   - Enhanced overall script performance and reliability, particularly for large datasets.

For more details, see the commit history or review the script annotations.
