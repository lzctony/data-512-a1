# Data 512 A1: Data curation
The goal of this project is to construct, analyze and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through Sepermber 30 2017. We are able to access the web data by using two different [Wikimedia REST API](https://www.mediawiki.org/wiki/REST_API) endpoins and combine different datasets from json formats into CSV in Python. Moreover, it we can followe the best practices for using pandas to manipulate the data frame and use matplotlib to generate a visulataion based on the output data file.

## License of The Source Data

There are 2 APIs we mainly use for this project. Here are the documentations, endpoints and terms.

* **The legacy Pagecounts API** ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end))

* **The Pageviews API** ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end))

* **Terms of Use** [(Wikimedia Foundation terms of use)](https://wikimediafoundation.org/wiki/Terms_of_Use/en)

## Pagecouts & Pageview Data
We collect the data for all months from both APIs in a Jupyter Notebook. Then save the raw results into 5 separate JSON source data files.
* **Pagecounts Data:** it provides access to desktop and mobile traffic data from January 2008 through July 2016. When collecting the pagecout data, it's different from the pageviews data, there is not parameter agent, so we don't have to choose.

* **Pageviews Data:** it provides access to desktop, mobile web, and mobile app traffic data from July 2015 through September 2017. When collecting the pageview data, we set the parameters agent' = user and 'granularity' = monthly. We excludes the spiders and crawlers when selecting the agent parameter.

## Final Data File
The final data file (**en-wikipedia_traffic_200801-201709.csv**) is comprised from 
* pagecounts_desktop-site_200801-201607.json
* pagecounts_mobile-site_200801-201607.json
* pageviews_desktop_201508-201709.json
* pageviews_mobile-app_201508-201709.json
* pageviews_mobile-web_201508-201709.json

We use **Jupyter Notebook** to write functions and use **Pandas** to manipulate those json datasets in order to achieve our output date file. The values of all variables of the final data file are shown below

* year: from 2008 to 2017
* month: from 01 to 12
* pagecount_all_views: sum of pagecount_desktop_views and pagecount_mobile_views
* pagecount_desktop_views: desktop traffic data from January 2008 through July 2016
* pagecount_mobile_views: mobile traffic data from January 2008 through July 2016
* pageview_all_views: sum of pagecount_desktop_views and pagecount_mobile_views
* pageview_desktop_views: desktop traffic data from July 2015 through September 2017
* pageview_mobile_views: mobile traffic data from July 2015 through September 2017

## Visualization
Here is the graph created by the final CSV file data. It shows the mobile traffic, desktop traffic and all traffic from Jan 2008 to Sep 2017 for both Pageviews and Pagecounts datasets respectively.

![alt text](https://github.com/lzctony/data-512-a1/blob/master/en-wikipedia_traffic.png)
