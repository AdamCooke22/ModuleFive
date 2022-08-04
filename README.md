# MODULE 5 CHALLENGE : Financial Planning Tools

In this challenge we are working at a fintech consulting firm that focuses on project to benefit local communities. Our first contract is with a large credit union. During this challenge we work on building a tool to help credit union members evaluate their financial health. The credit union wants their members to be able to do two things; assess their monthly budgets, and forecast a reasonably effective retirement plan based on their current holdings. What we created for this project was a financial planner for emergencies and a financial planner for retirement. 

To evaluate the crypto wallets and investment portfolios of members we need to use the requests.get() function to make an api call to get us the current prices of BTC and ETH. We then use a the json.dumps() to get that information into a dictionary that we can work from. To calculate the value of the stocks we need to use the tradeapi.REST() object to so that we can set the variables for our keys. We go on to set our tickers, timeframe (which is only 1 day) and the start and end date. Then we use the .get_bars() function to pull that information, then we reorganize the dataframes to drop the symbols so that we can use the pd.concat() function to combine the two dataframes into one. We then navigate the dataframe to find the closing value of the investments and multiply that by the number of shares to get the current valuations. 

To evaluate the emergency fund we created a list that contains that total value of a member's crypto wallet and investment portfolio. Then we create a data frame from that list so that we can use the .plot.pie() function to help us visualize the entire portfolio composition. To see if members could possibly create an emergency fund we use an if elif and else function with a few conditional statements to see if members have enough money, or show them how much they would need to create an emergency fund.

To create a financial planner for retirement we are going to use a monte carlo simulation. To get the data to run our simulation we want to get 3 years of historical data, so we adjust the starting and ending date of our api call to reflect 3 years from the date that we are looking at. Just as we did previously we use the get_bars() function, reorganize the dataframes, and concantenate the dataframes into one. We then use the MCSimulation() function while specifying the weights, number of trading days and simulations. To help us visualize these results we use the .plot_simulation() function and the .plot_distribution() function to show us a line plot of the results and a histogram that shows us the probability distribution of the simulation. To get more valuable data for this simulation we used the .summarize_cumulative_return() function that gives ust the mean, std, max, min, and the two most important peices of information, the 95% CI lower and upper. Those show us where we would most likely see our returns after 30 years. To do the simulation for 10 years we would do the exact same process, except we would change the timeframe and the weights to see if its possible to retire after only 10 years with a portfolio mostly weighted towards stocks.

---

## Technologies

This project leverages python 3.7 with the following packages:

* [Pandas](https://github.com/google/pandas) - Pandas is a powerfull tool for data analysis and manipulation. Pandas provides a plethora of useful functions that make it easy to express, analyze, and manipulate data.

* [Os](https://github.com/google/os) - This module provides a portable way of using operating system dependent functionality.

* [Requests](https://github.com/google/requests) - This Module allows you to send HTTP requests using python. The HTTP request returns a Response Object with all the response data (content, encoding, status, etc).

* [Json](https://github.com/google/json) - This module allows you to get data into a dictionary. Json is a syntax for storing and exchanging data. Json is text, written with JavaScript object notation.

* [Dotenv](https://github.com/google/dotenv) - Python-dotenv reads key-value pairs from a .env file and can set them as environment variables.

* [Alpaca_trade_api](https://github.com/google/alpaca_trade_api) - This is a python library for the Alpaca Commission Free Trading API. It allows rapid trading algo development easily, with support for both REST and streaming data interfaces. 

* [MCForecastTools](https://github.com/google/MCForecastTools) - This module allows for us to build a Monte Carlo simulation to predict the range of potential values for a portfolio.
---

## Installation Guide

Before running the application first install the following dependencies.

```
import os
import requests
import json
import pandas as pd
from dotenv import load_dotenv
import alpaca_trade_api as tradeapi
from MCForecastTools import MCSimulation

%matplotlib inline
```

---

## Usage

To use the Financial Planning Tools file simply clone the repository and open the financial_planning_tools.ipynb file in Jupyter Notebook.

Upon opening the file you will have the option to run the whole note book and that will provide you with all of the calculations, evaluations, and visualizations for the valuations of crypto wallets and investment portfolios. Determining if members have enough to build an emergency fund into their financial plan, and forecasting of the cumulative returns of retirement portfolios.


This is where we used the json.dumps function to review the response data from the api call we used for BTC.![Screenshot 2022-08-03 193852](https://user-images.githubusercontent.com/107158380/182755890-ef8acb8d-ccfc-4d78-b0b7-1ef42b369ece.png)

This is where we used the json.dumps function to review the response data from the api call we used for ETH.![Screenshot 2022-08-03 193923](https://user-images.githubusercontent.com/107158380/182755928-f64a6925-1048-4cd6-9a41-faf81a6da32b.png)

This is where we displayed the dataframe of the investment portfolio after reorganizing and concatenating the two dataframes from each ticker.![Screenshot 2022-08-03 193950](https://user-images.githubusercontent.com/107158380/182756118-5b3adf38-b4f5-4a7e-abe5-05ff14898352.png)

This is where we displayed the dataframe of the list of the entire financial assets data, the crypto wallet and the investment portfolio.![Screenshot 2022-08-03 194116](https://user-images.githubusercontent.com/107158380/182756337-fbd04482-84cd-4e38-a546-a374fb74a3e7.png)

This is where we plotted a pie chart of that dataframe to help visualize the composition of the member's entire portfolio.![Screenshot 2022-08-03 194143](https://user-images.githubusercontent.com/107158380/182756453-b722f6c0-7376-4d17-95a7-73cef27d881c.png)

This is where we displayed the dataframe of the historical data/closing prices after reorganizing and concatenating the two dataframes from each ticker.![Screenshot 2022-08-03 194222](https://user-images.githubusercontent.com/107158380/182756714-165bb78f-5a8d-4f0c-abea-a4731aba7c68.png)

This is where we displayed the 30 year simulation dataframe after running our simulation. ![Screenshot 2022-08-03 194256](https://user-images.githubusercontent.com/107158380/182756958-709bf833-54ab-4e6e-80ae-34f73331eebe.png)

This is where we used the calc_cumulative_return() function to get the cumulative returns of each simulation. ![Screenshot 2022-08-03 194409](https://user-images.githubusercontent.com/107158380/182757167-86bebaee-9dc0-4e30-9e9f-8adf149d26ef.png)

This is where we displayed the simulated cumulative returns of the thirty year simulation with a line plot. ![Screenshot 2022-08-03 194438](https://user-images.githubusercontent.com/107158380/182757264-a18406b9-4e3d-4306-bd89-f5988ec05b07.png)

This is where we displayed the probability distribution of the thirty year simulation with a histogram.![Screenshot 2022-08-03 194502](https://user-images.githubusercontent.com/107158380/182757413-55a44ce2-f462-40fd-aff5-e638c773f34a.png)

This is where we displayed the summary statistics of the cumulative returns of the thirty year simulation.![Screenshot 2022-08-03 194523](https://user-images.githubusercontent.com/107158380/182757505-383ade7f-9385-482b-8088-180f1c0e868e.png)

This is where we displayed the 10 year simulation dataframe after running our simulation.![Screenshot 2022-08-03 194608](https://user-images.githubusercontent.com/107158380/182757570-495b1b48-53c0-43d0-8db1-81a1b8c9e462.png)

This is where we used the calc_cumulative_return() function to get the cumulative returns of each simulation.![Screenshot 2022-08-03 194629](https://user-images.githubusercontent.com/107158380/182757629-7d8fc93c-672e-4cfb-b7a0-ed993d6522af.png)

This is where we displayed the simulated cumulative returns of the ten year simulation with a line plot.![Screenshot 2022-08-03 194650](https://user-images.githubusercontent.com/107158380/182757672-79a781fa-e270-465d-9389-9d160f7fa307.png)

This is where we displayed the probability distribution of the ten year simulation with a histogram.![Screenshot 2022-08-03 194707](https://user-images.githubusercontent.com/107158380/182757756-91cbd4bc-f68e-47cf-8a9f-e384bbc3688a.png)

This is where we displayed the summary statistics of the cumulative returns of the ten year simulation.![Screenshot 2022-08-03 194730](https://user-images.githubusercontent.com/107158380/182757801-ccd4695f-b4ce-4b4b-bc9b-4b0fb0887bf6.png)


It is not that simple when trying to invest for retirement. TIME is the biggest factor when it comes to investing for someone's retirement. Weighting the porfolio more heavily to stocks has the potential for a higher reward, but that comes with the higher risks that are associated with that. The CI lower and upper for the 10 year majority stocks portfolio are much lower than that of the 30 year balanced portfolio. It really would not be reccomended to invest mostly instocks unless you are really young or trying to play catchup. What is really recommended for investing in someone's retirement is to invest as much as you can as soon as you can. Trying to weight your portfolio more heavily to stocks is not something you want to do if you want to retire in ten years, because it is way too risky and as seen from this example, you are pretty much not even able to retire after ten years in the best case scenario, and in the worst case scenario you are going to have to give up your plan of retirement.

---

## Contributors

Completed by Adam Cooke

---

## License

MIT
