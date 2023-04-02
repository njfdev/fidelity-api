# Historical Data API

Fidelity has a "fastquote" API used on its website that fetches historical data for a company given its ticker symbol. This API does **not** require a Fidelity account.

## API Endpoint

```
https://fastquote.fidelity.com/service/marketdata/historical/chart/json
```

### Parameters

- `symbols` (**REQUIRED**): The ticker symbol of the stock (capitalization doesn't matter). Can also be a comma separate list of multiple ticker symbols.
  - Examples: `AAPL`, `aapl`, `F`, `AAPL,F`, `MCD,aapl`
- `productid` (**REQUIRED**): Not sure exactly what this does (probably for backend analytics), however, setting it to `researchexperience` works fine.
- `callback` (**REQUIRED**): Not sure why this exists, but it is required. Can be set to anything and just wraps the json response in a function call.
  - Examples: `data`, `result`
- `barWidth` (**REQUIRED**): The intervals for each "bar" of the data.
  - `1-60` (Intraday): The length of each interval in minutes.
  - `DAILY`, `WEEKLY`, `MONTHLY`, `QUARTERLY`, or `YEARLY` (Not Intraday): The names are self-explanatory.
- Date Range (**REQUIRED**)
  - The Fidelity API has 2 ways to select your date range. The first is using a `startDate` and an `endDate`. The second option is using `numDays`, however, that only works for intraday intervals.
  - `startDate`: The start of your range with the URL encoded date in the format `yyyy/mm/dd-hh:mm:ss` (zero padding is optional).
    - Examples: `2023/03/02-2:44:36`, `2023/3/2-2:44:36`
  - `endDate`: The end of your range with the URL encoded date in the format `yyyy/mm/dd-hh:mm:ss` (zero padding is optional).
    - Examples: `2023/03/02-2:44:36`, `2023/3/2-2:44:36
  - `numDays`: A number of how many days since now to fetch. Only works on intraday time frames.
    - Examples: `1`, `7`, `30`
- **TODO: Document the optional parameters**

### Response

**TODO: Document response object**

### Examples

Fetching the daily stock price from Apple (AAPL) during 2022:
```
https://fastquote.fidelity.com/service/marketdata/historical/chart/json?symbols=AAPL&productid=researchexperience&callback=data&barWidth=DAILY&startDate=2022%2F01%2F01-00%3A00%3A00&endDate=2022%2F12%2F31-24%3A59%3A59
```

Fetching the minutely stock price for Ford (F) and McDonalds (MCD) during January 2023:
```
https://fastquote.fidelity.com/service/marketdata/historical/chart/json?symbols=F,MCD&productid=researchexperience&callback=data&barWidth=1&startDate=2023%2F01%2F01-00%3A00%3A00&endDate=2023%2F1%2F31-24%3A59%3A59
```
