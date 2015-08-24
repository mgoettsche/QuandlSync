# QuandlSync: Keep up-to-date copies of Quandl collections.

_QuandlSync_ is a Python-based utility for keeping a local copy of Quandl collections. 
While Quandl's API makes it easy to download single datasets and even performs basic pre-processing,
there is no way to automatically fetch a whole collection or read its metadata. For
batch-style jobs that are run every time new data is added it is handy to keep a copy instead of
downloading the data in whole again.

_QuandlSync_:

- Downloads metadata of the collections you are interested in.

- Downloads all datasets of the collections or updates them if they are already present.

- Executes download calls in parallel to save time (but only with few threads, we don't want
to annoy Quandl who offer a great service).

- Updates in a traffic-saving way by only fetching differences since the last update.

The data is stored in the __collections__ sub-directory. 

## Prerequisites 
In addition to Python _3.x_ Quandl requires the following packages:

- pandas

- Quandl

You can download these packages from PyPi.

Also, you may want to register for a free Quandl account as the number of API calls per day is
very limited for anonymous users while it is currently 50000/day for registered users.

## Download and Installation
Simply check out the repository and move it to your preferred location.

## Configuration
Update _settings.json_ with the API key of your Quandl account and set the collections list
to contain the datasets you want to download. 

Example:

    {
        "api\_key": "YOUR\_API_KEY",
        "collections": [
            "BOE",
            "STOCKNOD",
            "CBOE"    ]
    }

Will download the collections "BOE", "STOCKNOD" and "CBOE". 

## Usage
Simply execute QuandlSync with:

__python3 QuandlSync.py__

## TODO

- Handle API call exceeding. Add queue system to account for usage cases in which a processing of the 
whole collection list is not possible in a single day due to the API call limit.

- Make the path for data download editable.
