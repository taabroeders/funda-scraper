# FundaScraper

This is a forked repository. Check-out the orginal code: https://github.com/whchien/funda-scraper
This version adds the ability to only scrape the newest houses on funda, by filtering how many days a property has been on the platform.

`FundaScaper` provides you the easiest way to perform web scraping from Funda, the Dutch housing website. 
You can find houses either for sale or for rent, and the historical data from the past few year are also attainable.

Please note:
1. Scraping this website is only allowed for personal use (as per Funda's Terms and Conditions).
2. Any commercial use of this Python package is prohibited. The author holds no liability for any misuse of the package.


## Install
You can clone the repository to your local machine with:
```
git clone https://github.com/taabroeders/funda-scraper.git
cd funda-scraper
export PYTHONPATH=${PWD}
```

## Quickstart 
```
from funda_scraper import FundaScraper

scraper = FundaScraper(area="amsterdam", want_to="rent", find_past=False, page_start=1, n_pages=3, min_price=500, max_price=2000)
df = scraper.run(raw_data=False, save=True, filepath="test.csv")
df.head()
```
![image](https://i.imgur.com/mmN9mjQ.png)


You can pass several arguments to `FundaScraper()` for customized scraping:
- `area`: Specify the city or specific area you want to look for, e.g. Amsterdam, Utrecht, Rotterdam, etc
- `want_to`: You can choose either `buy` or `rent`, which finds houses either for sale or for rent. 
- `find_past`: Specify whether you want to find the data in the past or the ones in the market. If `True`, only historical data will be scraped. The default is `False`.
- `page_start`: Indicate which page you want to start scraping. The default is `1`. 
- `n_pages`: Indicate how many page you want to scrape. The default is `1`. 
- `min_price`: Indicate the lowest amount for the budget
- `max_price`: Indicate the highest amount for the budget
- `days_on_funda`: Indicate the maximum nubmer of days the property can have been listed on the platform. 

The scraped raw result contains following information:
- url
- price
- address
- description
- listed_since
- zip_code 
- size
- year_built
- living_area
- kind_of_house
- building_type
- num_of_rooms
- num_of_bathrooms
- layout
- energy_label
- insulation
- heating
- ownership
- exteriors
- parking
- neighborhood_name
- date_list
- date_sold
- term
- price_sold
- last_ask_price
- last_ask_price_m2
- city

You can use `scraper.run(raw_data=True)` to fetch the data without preprocessing.

## More information

You can check the [example notebook](https://colab.research.google.com/drive/1hNzJJRWxD59lrbeDpfY1OUpBz0NktmfW?usp=sharing) for further details. 
Please give me a [star](https://github.com/whchien/funda-scraper) if you find this project helpful. 


