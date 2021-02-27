Python 3.8.6
# COVID-19_AMS
# What fraction of the basic reproduction number "R" of COVID-19 in The Netherlands is explained by the number of positive tests in the municipality of Amsterdam?
## A study of correlation using daily Dutch COVID-19 data of the National Institute for Public Health and the Environment (RIVM)

### Dependencies

- Python 3.8.6

	- jupyter 1.0.0
	- notebook 6.2.0
	- IPython 7.20.0
	- numpy 1.20
	- pandas 1.2.1
	- bokeh 2.2.3

### Programming 1 final project of Master Data Science for Life Sciences

- State the region and the domain category that your data sets are about

	The datasets from the RIVM contain data about COVID-19 (epidemic data) in the region of the Netherlands on municipality level

- State the research question

	What fraction of the basic reproduction number "R" of COVID-19 in The Netherlands is explained by the number of positive tests in the municipality of Amsterdam?


- Justify the chosen data storage and processing approach

	Data can be downloaded from the following links in CSV- and JSON-format.

	- https://data.rivm.nl/geonetwork/srv/dut/catalog.search#/metadata/ed0699d1-c9d5-4436-8517-27eb993eab6e
	- https://data.rivm.nl/geonetwork/srv/dut/catalog.search#/metadata/5f6bc429-1596-490e-8618-1ed8fd768427

	Data is not kept in Github because of size limitations. All data is processed programmaticaly with Pandas.	

- Justify the chosen analysis approach
	
	Analysis was done by firstly exploring both datasets (reproduction number dataset and positive tests dataset). Data was sampled from daily to weekly to get less variance between datapoints. 
	
	Here after the amount of positive cases in amsterdam was compared to expected amount of positive cases in amsterdam based on population assuming COVID-19 cases are uniformly distributed through-out the Netherlands.
	The absolute change in positive cases between datapoints was calculated and data before the 12th of june 2020 was removed. This was done because the R before the 12th of june was calculated based on number of hospital admissions
	And was not deemed accurate enough. For our research questions we look at the R calculated based on positive cases (after 12th of june 2020). 
	
	Subsequently the correlation between the R variables, absolute change in positive cases, total positive cases, deaths and hospital admissions were visualized. As expected the lower and upper bound of R correlate highly with the 
	average R, while the second cluster of correlation is visible in the deaths, hospitalisations and total reported positive cases.
	Finally the R was plotted against the absolute change in positive cases for both the Netherlands (including Amsterdam) and the municipality of Amsterdam. By taking the fraction of the slope of Amsterdam compared to the 
	Netherlands the conclusion was reached. **Since 2020-06-12 until 2021-02-22, 8.43% of the reproduction number R of COVID-19 in the Netherlands can be explained by positive cases in Amsterdam.
	As of 2020, Amsterdam accounts for 5.01% of the population of the Netherlands.**

- Justify the chosen data visualization approach

	All data was visualized in a jupyter notebook with the Bokeh visualization library.
