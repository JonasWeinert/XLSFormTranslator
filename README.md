# XLSForm Translator App

This is a python application that helps in translating XLSForm documents from English to a target language of your choice using Google's translation API. It is especially useful for researchers or data scientists who deal with XLSForm documents in different languages.


#### ⭐ If you like this tool, please give it a star:-)


## Prerequisites

The application requires the following:

- Python 3.6 or higher.
- Pandas Python Library.
- Google Cloud Translate API.
- Google Cloud SDK for setting up credentials.

## Installation

- Fork this repository.
- Install the required Python libraries. For this, you can use the command: `pip install pandas google-cloud-translate openpyxl`

## Setup

To use this script, you need to set up Google Cloud Translate in your environment:
1. Set up a Google Cloud Project: Follow the guide [here](https://cloud.google.com/translate/docs/setup).
2. Enable the Google Cloud Translate API for your project. You can get a free API key [here](https://cloud.google.com/docs/authentication/api-keys#console)
3. Create a service account and download the JSON credentials file.
4. Upload your Google translate API authentication JSON file in the directory and rename it to `authentication.json`.
5. Enter your desired output language code (eg. `fr` for French) in the next cell. A list of codes can be found here: https://developers.google.com/admin-sdk/directory/v1/languages
```
Note: You can only translate into one language at once. If you want to translate multiple languages you can either repeat the process or modify the code to add a loop in Cell 5.
```
Make sure that your XLSForm 
1. has a column with english wording that is called ***label::English***;all of these sheets: `survey`,`choices`,`settings`.
2. is called `thefile.xlsx` and uploaded in the directory.

After that, Execute all cells.


## The code

To use this script:

1. Load your XLSForm document into a pandas DataFrame. The script currently assumes you have three DataFrames: 'dfsurvey', 'dfchoices', and 'dfsettings'. Each of these correspond to a worksheet in your XLSForm document.

2. Call the `translate_dataframe()` function for each DataFrame, passing the DataFrame and the name of the column that contains the text to translate. Currently, the script assumes this is 'label::English', but this may vary depending on the structure of your XLSForm document.

3. The script will translate the text in chunks, add the translations to a new column in the DataFrame, and replace any 'nan' strings with NaN values (missing data indicators in pandas).

4. The script then writes the translated DataFrames back to an Excel file using the 'openpyxl' engine. You can specify the name of this file with the 'name' variable.

## Note

The script currently assumes that the text to translate is in English, but this can be modified according to your needs.

The script also uses '<sep>' as a separator when joining and splitting the chunks of text. Ensure that your original text does not contain '<sep>', or this could cause issues with the translation.

This application only translates text in existing columns of your DataFrames. If you want to add new columns with translated text, you need to modify the `translate_dataframe()` function accordingly.

The script also does not handle API request errors. Depending on the size of your text and the limitations of your Google Cloud account, you may need to handle these.

## Contributions

Feel free to contribute to this project by opening issues or submitting pull requests. Any contributions you make are greatly appreciated.
