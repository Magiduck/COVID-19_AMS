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

### Optional dependencies (if plots are too large for notebook or code gets cut-off)

- jupyterthemes 0.20.0
	- After which you can run *jt -t onedork -fs 95 -altp -tfs 11 -nfs 115 -cellw 88% -T*

### Programming 1 final project of Master Data Science for Life Sciences

- State the region and the domain category that your data sets are about

	The datasets from the RIVM contain data about COVID-19 (epidemic data) in the region of the Netherlands on municipality level

- State the research question

	What fraction of the basic reproduction number "R" of COVID-19 in The Netherlands is explained by the number of positive tests in the municipality of Amsterdam?


- Justify the chosen data storage and processing approach

	Data can be downloaded from the following links in CSV- and JSON-format.

	- https://data.rivm.nl/geonetwork/srv/dut/catalog.search#/metadata/ed0699d1-c9d5-4436-8517-27eb993eab6e
		- Direct link: https://data.rivm.nl/covid-19/COVID-19_reproductiegetal.json 	
	- https://data.rivm.nl/geonetwork/srv/dut/catalog.search#/metadata/5f6bc429-1596-490e-8618-1ed8fd768427
		- Direct link: https://data.rivm.nl/covid-19/COVID-19_aantallen_gemeente_per_dag.csv 	

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
	As of 2020, Amsterdam accounts for 5.01% of the population of the Netherlands.** Further research is needed to interpret if this is as expected or not.

- Justify the chosen data visualization approach

	All data was visualized in a jupyter notebook with the Bokeh visualization library and can be found under the directory *final_visualizations*. Further captions explaining the plots can be found under *analysis.ipynb* 

	**Plot 1**: The reproduction number was plotted in a line plot of the average with a 95% confidence band around it based on the 'R_up' and 'R_low' provided in the dataset from the RIVM. The R value of 1 is drawn into the plot because of the nature of R to decrease below 1 and increase above 1 by itself. Also annotateed is the change in methods for the calculation of R on the 12th of june 2020.

	**Plot 2**: The total number of new COVID-19 cases for Amsterdam vs. other municipalities in the Netherlands was plotted in a scatter plot. A scatter plot was chosen because in this plot each dot represents a day for a municipality creating a lot of data points, too chaotic for a line plot.

	**Plot 3**: The absolute change in COVID-19 cases per day in Amsterdam vs other municipalities in the Netherlands. By plotting the other municipalities together in a scatter plot you can already roughly see the contribution of positive cases in Amsterdam to the positive cases in the Netherlands. It also shows that the daily data varies greatly between subsequent datapoints.

	**Plot 4**: This plot serves as a zoom in of the previous plot in which the outliers are removed to look closer to the average pattern of absolute change in COVID-19 cases.

	**Plot 5**: This plot shows the same data as plot 3 but sampled weekly. This shows that weekly sampling removes a lot of variability between datapoints and shows a clearer trend. It is seen that in the first wave Amsterdam did not contribute that much to the number of total positive cases while in the second wave they do.

	**Plot 6**: The total number of new COVID-19 cases per day in the Netherlands and Amsterdam. In this plot it was chosen to visualize the total number of new COVID-19 cases per day in areas. This creates a clear overview of the contribution of positive cases of Amsterdam to the positive cases in The Netherlands. An orange line was drawn toshow the expected number of positive cases in Amsterdam based on the total number of cases in the Netherlands and the proportion of the Dutch population living in Amsterdam. This line somewhat follows the real number of positive cases with periods in which the number of expected cases is higher and lower than the real number of positive cases.

	**Plot 7**: The comparison between the average reproduction number R vs. the absolute change of new COVID-19 cases. The very horizontally flat line suggests that the higher the R in the Netherlands does not particularly mean the higher the number of new COVID-19 cases in Amsterdam. By taking the difference between the first coefficient of the linear regression of the Netherlands and Amsterdam you can (naively) tell the contribution of the positive cases in Amsterdam to the R in the Netherlands.

	**Plot 8**: This plot is the same as plot 7 but with outliers trimmed off.
