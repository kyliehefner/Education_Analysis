# Column Definitions

## EdStatsData / indicators_df
### Indicator measurements by country and year (69 columns, 886,930 rows)

Country Name: Same as EdStatsCountry Table Name (foreign key)

Country Code: Same as EdStatsCountry Country Code (foreign key)

Indicator Name: Same as EdStatsSeries Indicator Name (foreign key)

Indicator Code: Same as EdStatsSeries Series Code (foreign key)

Years columns: 1950 - 2017 (actual numbers), then 2020 - 2100 by 5s (projected)
Year columns are 73-96% null (1990: 86%, 1995: 85%, 2000: 80%, 2005: 79%, 2010: 73%)

## EdStatsSeries / series_df
### Information about each of the 3,665 indicators (20 columns, 3,665 rows)

**Series Code: all unique, primary key**

Topic: General category, 37 unique

Indicator Name: all unique, name and description for series code (primary key)

Short definition/Long definition: indicator description 41% of short definition is null

Unit of measure/Limitations and exceptions/Notes from original source/General comments/Development relevance: all null

Periodicity/Base Period/Other notes/Aggregation method/Related source links: 97%/91%/85%/99%/94% null

Source: 31 unique

Statistical concept and methodology: 99% null, but includes "TIMSS"

The last 3 columns are all null

## EdStatsCountry / country_df
### Information about each of the 241 countries (31 columns, 241 rows)

**Short Name/Table Name/Long Name: Country name (primary key)**

Country Code/2-alpha code/WB-2 code: Country code (primary key)

Currency unit: name of currency (11% null)

Special Notes: 40% null, not needed

Region: 7 unique regions (11% null)

Income Group: Low income, Lower middle income, Upper middle income, High income: nonOECD, High income: OECD (GNI per capita) (11% null)

21 other categories

## EdStatsCountry-Series / country_series_df
### Which series codes we have for each country (3 columns, 613 rows)

CountryCode: 3-letter code for country (foreign key)

SeriesCode: (foreign key)
- SP.POP.TOTL = Population, total (counting all residents regardless of citizenship)
- SP.POP.GROW = Population growth (annual %)
- NY.GDP.PCAP.PP.CD = GDP per capita based on purchasing power parity (current international dollars)
- NY.GDP.PCAP.PP.KD = GDP per capita based on purchasing power parity (constant 2011 international dollars)
- NY.GNP.PCAP.PP.CD = Gross national income per capita based on PPP (current international dollars)

DESCRIPTION: Where the seriescode data comes from

## EdStatsFootNote / footnote_df
### Glossary for country, seriescode, and years (4 columns, 643,638 rows)

Country code: 239 unique (all but 2 countries) (foreign key)

SeriesCode: 1,558 unique (most of the series) (foreign key)

Year: 56 unique, YR1970 - YR2050 (projections)

Description: 9,120 unique, where the seriescode data comes from

# Cleaning notes
- EdStatsCountry-Series:DESCRIPTION has some with an extra space at "Data sources :"
- There is one extra unique country name and country code in the edstatsdata table than the country data table, maybe a typo?