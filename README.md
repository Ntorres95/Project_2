# Project_2

ETL Code Jupyter Notebook contains our main code.

Extract - sources of data that we extracted from 

Data sources are taken from an existing Kaggle account. CSV files are saved in our “Resources” folder in our Github repository. There are a total of three CSV files, listings.csv, calendar.csv, and review.csv.
To extract all of the csv files we “import pandas as pd” and use the “pd.read_csv(...)” function to transfer our files into a database.

listings_file = "Resources/listings.csv"
listings_df = pd.read_csv(listings_file)

calendar_csv = "Resources/calendar.csv"
calendar_df = pd.read_csv(calendar_csv,encoding="utf8")

review_data = pd.read_csv(file_to_load,encoding="utf8")
review_data.head()

Extracting the CSV files into a dataframe allowed us view the data sets in its entirety so that we can determine which tables would be necessary for further analysis. 





Transform

We took our data from the three CSV files - Reviews, Listings, Calendar - and created a set of rules or objectives in order to transform them into what we wanted.  
Our objective was to create a list of top-rated airbnb listings in and around Boston with relevant booking information for prospective, hypothetical clients.
We decided that we wanted to only have the clean data with these specifications:
1. We wanted only quantifying information in our dataset, no comments, review blurbs, etc.
2. Specific information on reviewers of listings or their reviews were not included
3. We wanted Airbnb listings with ratings greater than 90.
4. We wanted data to be in specific formats.  Dates in datetime, numbers in int etc.
5. Full information: no empty cells.

We cleaned up our data as follows:

reviews.cs

Dropped any data with empty data cells.
Eliminated the “comments” column.
Converted the string dates to datetime format.
Grouped data by listing_id for easier access.
Looked at review counts by listing id

calendar csv

Converted string dates to datetime format.
Converted available data output to boolean.
Cleaned price column to clean numeric values.

Listing.csv

Merged with calendar on listing id.
Eliminated 91 irrelevant columns.
Dropped any duplicates and empty rows.
Filtered data, leaving listings with ratings greater than 90.
Dropped any duplicate listings/dates, only keeping the latest ones.
Important columns: "id", "listing_url", "name", "price_y", "number_of_reviews", "review_scores_rating", "date", "available"

Load

We decided to choose 2 tables for the end product: reviews and listings, where listings was a joined table between “calendar” and “listings”.
We decided on formatting the information into these 2 tables with the following reasons:
1. We wanted one table, listings, to show the quick summary information that we thought our hypothetical clients wanted to see, so that they could make a quick decision to bookings.
2. We also wanted another table that gave them access to the review information, reviews, just in case they would be interested in viewing that, without having an overwhelming amount of data.
We decided to load these 2 tables in SQL for these reasons:
1. SQL has power to easily manage and filter our relatively large dataset.
2. Our 2 datasets have a specific data relationship, and we thought it best to use SQL to store this relationship.
