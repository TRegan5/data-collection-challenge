# data-collection-challenge
Webscraping the Mars News site for article titles and preview text and Mars Temperature Data site for multiple datapoints relating to temperature and atmospheric pressure recordings from the Curiosity rover. 

## Part 1: Scrape Titles and Preview Text from Mars News
After analyzing the Mars News site using DevTools, I scraped for all titles and preview text targeting information by the class "list_text" and storing in one object. 

Within this extracted data, I was able to target titles and previews with the classes "content_title" and "article_teaser_body," respectively, looping through all elements in the original object. 

## Part 2: Scrape and Analyze Mars Weather Data
### Step 1: Visit the Website
I made one addition to the provided code, building in a delay for loading the page. Using DevTools, I analyzed the Mars Weather Data site and determined each row of the Mars Temperature Data could be extracted by targeting targeting the class "data-row."

### Step 2: Scrape the Table
I created a BeautifulSoup object and extracted all the rows from the Mars Temperature Data table. 

### Step 3: Store the Data
To store the data, I used a nested for loop to sequence through each element in each row, and then each row from the table to append each required piece of data to a dictionary for each row and each dictionary to a table for the entire table. However, I noticed that my iteration included coding for the line breaks and cells within the table. Following this analysis, I specified each element to skip these formatting strings. 

Once complete, I converted the list of dictionaries to a pandas DataFrame. 

### Step 4: Prepare Data for Analysis
I examined the data types for each column in the new dataframe and used astype to cast appropriate new data types. 

### Step 5: Analyze the Data
1. How many months are there on Mars?
Using value_counts, I can see that the data records for 12 Martian months.
2. How many Martian days' worth of data are there?
Using the .count() function for sol data, I can see there are 1867 Martian days recorded in the data.
3. What is the average low temperature by month?
Grouping by month, and applying .mean() to the "min_temp" column, I was able to plot and sort the data to determine months 3 and 4 are the coldest month, while months 8 and 9 are the hottest (i.e. least cold).
4. Average pressure by Martian month
Grouping by month and averaging pressure with .mean(), I was able to plot and sort the data to determine that months 6 and 5 have the lowest atmospheric pressure while month 9 has the highest. 
5. How many terrestrial (earth) days are there in a Martian year?
Knowing that lowest temperatures occurred during month 3, I can exemine a plot of the Minimum Temperature vs. Number of Terrestrial Days to find the lowest temperatures visually. It appears that the two lowest points occur around 450 and 1080, indicating a cycle from month 3 back to month 3. This difference suggests a Martian year lasts 630 terrestrial days. 
### Step 6: Save the Data
Using Pandas function .to_csv, I exported teh mars_df dataframe to mars_data.csv in the Output folder. 