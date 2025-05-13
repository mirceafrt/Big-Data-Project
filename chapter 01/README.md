# Data Warehousing

## Scenario
You are a Data Engineer in the InternIT company. The InternIT company is a Romanian StartUp in **online banking** and offers banking services for the customers.

## Business requirements
InternIT company provides a financial platform for currency transactions and financial consultance for their customers.

### Core Business Goals
1. **Currencies analysis** - Aggregate currencies evolution
2. **Curencies insights** - Track trends for currencies in demand
3. **Prices trends** - Provide benchmarks for different currencies
4. **Currencies popularity** - Determine which currencies are most in demand

#### Reports
Buy transactions by currency.\
Sell tranasactions by currency.\
Price evolution of top 10 currencies.

#### Dashboards
Current RON price vs other currencies.\
Maximum and minimum price on current day of the RON.\
Historical price evolution of the RON.

#### KPIs
Total currencies transactions.\
Average transaction amount.\
Top 10 amount transactions on buy.\
Top 10 amount transactions on sell.

## Data Warehouse Design
It has a server `InternIT` and a database named `intern_it`.

### Sources
The data sources for the company are:
- InternIT - Own Platform data.
- [ExchangeRate](https://www.exchangerate-api.com/) - Partner Platform for today traditional currencies rates.
- [XE](https://www.xe.com/symbols/) - Partner Platform for currencies names and symbols.

#### InternIT source
`internit_data`

#### ExchangeRate source
`exchange_data`

| Column Name | Data Type | Description |
| - | - | - |
| time_last_update_unix | TIMESTAMP | Unix timestamp from when data are available |
| time_next_update_unix | TIMESTAMP | Unix timestamp until when data are available |
| base_code | VARCHAR(3) | Reference currency code |
| currecny_code | VARCHAR(3) | Standard currency code |
| currency_rate | DECIMAL | Price of the currency vs reference currency |

#### XE Source
`xe_data`

| Column Name | Data Type | Description |
| - | - | - |
| country_and_currency | VARCHAR(50) | Country and currency name |
| currency_code | VARCHAR(3) | Standard currency code |
| font_code | TEXT | Reference currency code |
| font_arial | TEXT | Standard currency code |
| unicode_decimal | TEXT | Deimal unicode of the currency |
| unicode_hex | TEXT | Hex unicode of the currency |
