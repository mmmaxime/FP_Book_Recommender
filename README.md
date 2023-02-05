# Iron Hack Final Project: Book Recommender
This project aims to run a book recommender based on the inputted book title and outputs 3 book title recommendations, its respective authors, genres, and book covers. This data was accumulated through two Kaggle datasets, and web-scraping using [Selenium](https://selenium-python.readthedocs.io/) and [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/). Here is the link to my Google Slides  [presentation](https://docs.google.com/presentation/d/1DpB_7iD-pqaU0gNgE7iDsF7sMrAUeTNN147uk_t6Wqk/edit?usp=sharing). 

## Motivation
Decided to further enquire on this topic, as before the Iron Hack Data Analytics Bootcamp my friends and I were organising a book club and since being in the bootcamp I haven't been able to enjoy said books. Now that the Bootcamp is over, I would be very much interested in restarting this book club and receiving recommendations based on titles and genres of books we previously liked.  

## Build Status
The code for this Jupyter Notebook is divided into parts: 
  - __Web Scraping:__ Web Scraping was done through the use of Selenium off of the Barnes & Noble website (link below), information such as title, author, year_published, isbn,    image_link, genre, description, publisher, page_count and rating were pulling and organized into a DataFrame. For the other 2 sets, they were pulled from the Kaggle website(links below).
  - __Data Cleaning and EDA:__ Divided into different book databases, then ultimately concatenating the data with columns: title, author, year_published, isbn,    image_link, genre, description, publisher, page_count and rating.
  - __Analysis/Recommender:__ Used the CountVectorizer recommender/model to analyse, cluster, and recommend books based on the user inputing a book title.
  - A large part of the book has repearted code

## Code Style
Used the Python 3 code in my Jupyter Notebook.

## Screenhots
![Screen Shot 2023-02-03 at 3 58 25 PM](https://user-images.githubusercontent.com/117981133/216635192-9e74001c-fca9-4a88-a20d-6aa9c48a7b32.png)
![Screen Shot 2023-02-03 at 4 01 59 PM](https://user-images.githubusercontent.com/117981133/216636080-24acca1b-ed76-4fa7-a2f7-a3c42e013907.png)
![Screen Shot 2023-02-03 at 4 02 46 PM](https://user-images.githubusercontent.com/117981133/216636282-25bb0e4d-6587-473a-afa1-a71c20431419.png)


## Tech/Framework used
I used Python, and ran the following librairies to help execute the code:
import time
import requests
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.metrics.pairwise import cosine_similarity
from sklearn.feature_extraction.text import CountVectorizer
import matplotlib.pyplot as plt
import imageio
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.keys import Keys
import time
import requests
from bs4 import BeautifulSoup as bs4

## Features
The features that were the main focus for the book recommender are: title, author, rating, genre, description, isbn, publisher, year_published, page_count, and image_link. 

## Code Examples
- *%%time
- *bookdata = final_data.drop(['isbn','year_published','page_count','description'],axis=1)
- *bookdata['data'] = bookdata[bookdata.columns[1:]].apply(
    - *lambda x: ' '.join(x.dropna().astype(str)),
    - *axis=1
- )*
- *print(bookdata['data'].head())*

## Installation
I already had Jupyter Notebook installed through my Anaconda Navigator, but I had to "pip install ChromeDriverManager" and "pip install selenium.webdriver" for the web-scraping. 

## API reference
Didn't use an API reference for this project as I used Selenium to web-scrape. 

## Tests
As previously mentioned, I used the CountVetorizer for my recommender/model. 
- Here is an example of the code used to run the recommender:

- *%%time
- try:
    - recommendations = pd.DataFrame(df.nlargest(4,input_title)['title'])
    - recommendations = recommendations[recommendations['title']!=input_title]
    - a = recommendations.index.values.tolist()
    - print('Here are some fun recommendations for you:')
    - display(pd.concat([recommendations,final_data.iloc[a][['author','genre']]],axis = 1))
    - b = bookdata.iloc[a]['image_link'].values.tolist()
    - for i in b:
        - plt.imshow(imageio.imread(i))
        - plt.show()*
    
- *except: 
    - print("Sorry, I don't have any book recommendations. You should go for a walk instead!")*

## How to use?
I would recommend first reading the _"Readme"_ before opening the .ipynb file. When going through the latter file, it is apparent to see how and why I decided to keep and delete certain values when cleaning the data. Upon the analysis, I further concatenated the data to later add to the recommender and to generate book suggestions. The whose process from scraping to recommending is broken up into 3 phases: Phase 1: Web-Scraping, Phase 2: Data Cleaning and EDA, and Phase 3: Recommender.

## Contribute
You can contribute by opening the _"Readme"_ file, clicking on _"Edit"_ and leaving a comment at the bottom of the document with your github link and suggested comments. 
Here is my github repository [link](https://github.com/mmmaxime?tab=repositories)

## Credits
I used the following websites for datasets:
- [Kaggle Dataset 1](https://www.kaggle.com/datasets/thedevastator/comprehensive-overview-of-52478-goodreads-best-b)
- [Kaggle Dataset 2](https://www.kaggle.com/datasets/dylanjcastillo/7k-books-with-metadata)
- [Barnes & Noble Top 100 Bestseller's list](https://www.barnesandnoble.com/b/books/_/N-1fZ29Z8q8)

## License
Used Python 3 License. 
