# Project Group 3 

Members: 
Youri Beijer 
Ecem Tyurkay 
Rico de Jong 
Saumitra Deo 
Pranshu Sharma 

Student numbers: 
4965027
6301207
5348870
6434223
6505015

# Research Objective

*Requires data modeling and quantitative research in Transport, Infrastructure & Logistics*

The aim of this report is to answer the following research question:

"How is rail freight distributed across European countries by consignment type and commodity group, and how does the railway network influence these patterns/trends?"

To address the main research question in a structured way, it is divided into several sub-questions, each focusing on a specific aspect of freight distribution, commodity and network influence.

1. How do different countries relate to different shares of consignment types?

2. How does network density influence consignment type? 

3. How does the network length influence the modal share?

4. How is rail freight activity distributed among EU countries, and which nations lead or lag in freight volume?

5. How has the trend of full train consignments changed over time in the top and bottom-five EU freight countries? (removed)

6. How do commodity groups (NST 2007 classification) influence the distribution of consignment types?


# Data Used

rail_go_consgmt – Goods transported by type of consignment (Eurostat).

rail_go_grpgood – Goods transported by group of goods (Eurostat, NST 2007 classification, from 2008 onwards).

rail_if_line_na – Length of electric and non-electric railway lines, by nature of transport (Eurostat).

Rail_go_total – Eurostat indicators for total freight transported.

tran_hv_frmod – Eurostat statistics on the modal split of freight transport.

ttr00006 - Total railway network length recorded and submitted to eurostat.

# Data Pipeline

**1. Data Collection**

Download datasets from Eurostat (rail_go_consgmt, rail_go_grpgood, rail_if_line_na, freight volumes, modal share).

Ensure consistent formats (CSV/Excel).

**2. File Path Setup**
Defined a base directory for Eurostat data files and safely constructed full file paths using os.path.join.
Created a dictionary (files) containing paths to all relevant Eurostat freight datasets (e.g., rail freight volumes, modal share, line length, consignment, and goods groups).

**3. Country Selection**
Defined an updated list of EU27 countries + Switzerland (as of 2025) for filtering and standardizing dataset coverage.
Excluded non-EU countries (e.g., turkey) to maintain consistency with EU-level statistics.

**4. Data Merging**
Standardize country names, years, decide on units for obs_values. Filter to the required timeframe (2008 onwards).
Append raw data obs_values to each collumn and appropriatlty name it.

The notebook for steps 1-4 can be found The notebook for steps 1–4 can be found [**here**](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Scripts/Preprocess_Eurostat_os_V2.ipynb), manually it can be found in the github in ../Scripts/Preprocess_Eurostat_os_V2.ipynb.


**5. Data Storage & Versioning**
Store cleaned datasets in your GitHub repository.

Each member works on a separate branch, commits changes, and documents preprocessing steps.

**6. Additional reviewing missing data_consignment**
Imported the merged Eurostat dataset, containing all harmonized freight transport indicators.

Conducted a coverage matrix analysis to assess data completeness across countries and years — identifying where observations were missing for specific variables.

**7. Curve fitting (interpolation of missing data)**
Applied curve fitting as the interpolation method to estimate missing data points within each country’s time series.

Fitted appropriate mathematical functions (e.g., polynomial or exponential) to the observed data of each geopolitical entity, capturing unique national freight trends.

Used these fitted models to estimate missing values for key variables such as freight volume, modal share, and railway network length.

**8. Calculate confidense for each fit**
For each fit, calculated and recorded the uncertainty as a standard deviation, providing a quantitative measure of confidence for the interpolated values.

This approach ensured that all time series were both complete and analytically robust, while maintaining transparency about estimation uncertainty.

Visual and statistical checks confirmed that fitted curves followed realistic data patterns and avoided overfitting.

**9. Exporting addition document for consignment data**
Exported the finalized, curve-fitted dataset, including respective uncertainty metrics,  into a standardized CSV file for analytical use.

Stored the cleaned data and corresponding uncertainty records in the project’s structured “cleaned data” directory, versioned on GitHub for reproducibility.

This notebook provides the final, validated dataset with documented uncertainty, forming the foundation for subsequent statistical, econometric, and visualization analyses.

The notebook for steps 5-9 can be found The notebook for steps 5–9 can be found [**here**](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Scripts/Cleaning_Eurostat.ipynb), manually it can be found in the github in ../Scripts/Cleaning_Eurostat.ipynb


# Data coverage

The missing data (Step 6) was analysed and converted into a coverage matrix.
![coverage_table_colored.png](attachment:coverage_table_colored.png)

This indicates that there is a clearlack of datain train consignment shares per  capita. These consignments will be fixed using a built in scipy function called curve_fitting.Curve fitting is the process of finding a mathematical function (a curve) that best describes the relationship between two variables in the data.

# Uncertainties

Step 7 of the data pipeline created some uncertainties. Even though minimal these should not be neglected in our study. The .csv files documenting these confidence intervals can be found [**here**](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Data/Sub-question-2/df_merged_cleaned.csv), manually it can be found in the github in ../Data/processed/merged_eurostat_clean_V2.csv
 

Each curve-fitted value has a standard deviation which is captured in their respectively named collumn. The values match up in rows with their curve-fitted counterparts. For example: The collumn uncertainty_estimate_NL refers to the uncertainty of network length values in the form of a standard deviation, the rows match up with the values curve fitted.

# Sub-questions

To address the main research question in a structured way, it is divided into several sub-questions, each focusing on a specific aspect of freight distribution, commodity and network influence. Hypotheses formed already regarding these sub-questions and statistical methods will be used to test validity of these questions.


# 1 How do different countries relate to different shares of consignment types?

Within the case of consignment types within countries in the European Union for rail freight, there are primarily 2 types of identifiable data present on Eurostat. They are:

**Full Train Load:**
This consignment type comprises a single type of goods being transported by a single train, within a single integrated consignment note and wagon lists.

**Full Wagon Load:**
This consignment type comprises multiple types of goods being transported within a single train, with various consignment notes and wagon lists.

The countries being considered here are given in the following table along with their country codes for easier identification.

| Country     | Code |
|--------------|------|
| Switzerland  | CH   |
| Germany      | DE   |
| Italy        | IT   |
| Poland       | PL   |
| Sweden       | SE   |
| Slovenia     | SI   |
| Slovakia     | SK   |

These countries have been chosen for the analysis as the data for these were available to a larger extent as compared to other countries from the European Union. Few countries had some data missing for some years and hence its data has been interpolated and extrapolated in those cases.\
\
Considering the case of full train loads, the following plot has been obtained for the following.

![newplot.png](attachment:newplot.png)

The output here describes the full train load that is carried in rail freight to the countries mentioned above. Here it is seen that Germany carries the largest quantity (Thousand Tonnes) of full train load consignment type while Slovenia has the least amount of full train loads being carried.Italy has shown a relatively steady increase in the amount of full load trains. Switzerland, Slovakia and Sweden have shown a steady trend of full train loads, with Slovakia showing signs of decline. Poland has witnessed a drastic drop from 2008 till 2009 but then gained it as quickly, showing resiliency. It remained stable before increasing and decreasing again till 2024, showing some signs of volatility even during its growth. Germany maintains the highest amount of full train loads. Germany having a large quantity of full train load indicates a large industrial presence within the country, which is expected and is required to meet the growing demands of it. An increasing demand from Italy also suggests a strong requirement for grains and industry raw materials or equipment for the country.

![newplot2.png](attachment:newplot2.png)

In the full wagon load consignments, Germany sees an overall increasing trend, barring the decline from 2017-2019 and again increasing since then. Switzerland, Slovakia, Slovenia and Italy have seen relatively lower levels of full wagon load consignments, which were decreasing. Poland has seen a drastic rise and fall in full wagon load consignments since 2010, which could be treated as an outlier considering the data trend thereafter. It continued to decrease further and brief periods of increase from 2016 till 2019. As from the previous graph, it becomes evident that Poland looks to shift to full train consignments instead to meet its demands and requirements.\
Sweden shows a modest rise in the use of full wagon loads , increasing from 23904 in 2012 to 31499 thousand tonnes in 2024, in full wagon load, marking an increase of 31.77 % in 12 years.

![newplot3.png](attachment:newplot3.png)

Through these graphs, we see that there is a growing demand for full train loads as compared to full wagon loads for industry and large-requirement centric countries such as Germany and Italy, as both display an increasing trend.\
Sweden, Slovenia and Slovakia have seen relatively stable freight volume trends, with some variations occurring in Sweden with respect to the Full wagon load consignment type (increasing trend).\
We also observe that the major share of freight consignments is dominated by Germany, then Poland,Italy and thereafter the remaining European countries.

**Conclusions**

The chi-square test shows a statistic of 495,479 with 6 degrees of freedom and a p-value of 0.0, indicating that countries differ significantly in their allocation of freight between Full Train Load and Full Wagon Load shipments.. The statistical test shows a significant relationship between country and consignment type distribution. Different countries exhibit distinct patterns in how they allocate freight between Full Train and Full Wagon loads. Italy uses full train loads for 92% of its rail freight, while Sweden uses them for 58%. Other countries fall in between. To conclude, the distribution of consignment types varies significantly across countries.

The notebook used to generate this answer can be found [**here**](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Scripts/Sub-question-1/Sub_Question_1.ipynb) ,manually in the github it is ../Scripts/Sub-question-1/Sub_Question_1.ipynb

The processed data file used is the same as the data file in sub-question 2.


# 2 How does network density influence consignment type? 

This section explores how differences in network density and the extent of the transport network relative to population and geographic area affect the distribution of consignment types across European countries. Network density reflects the accessibility and capacity of the transport system, which can influence how freight is typically moved. 

**Data usage.**

All available data across the full time period were used in this analysis. Since the purpose of this sub-question is to test the relationship between network density and the distribution of consignment types rather than changes over time. Temporal variation is not relevant here. Including all years increases the robustness of the analysis by capturing the full range of observations. The evolution of these trends over time will be examined in a later sub-question, where temporal effects are explicitly considered. Two complementary measures of network density were used to capture different aspects of rail infrastructure distribution.

**Population-based network density** reflects the accessibility of the network to people. It provides insight into how well the existing infrastructure serves demand that originates from population concentration for instance, in densely populated countries where rail networks are heavily used for both passenger and freight transport.

**Area-based network density** captures the spatial coverage and physical extent of the network. This measure is important for understanding how the network supports long-distance freight operations and regional connectivity, especially in geographically large countries where infrastructure spread across an area determines freight mobility potential.


By comparing both density types, it becomes possible to distinguish between the effects of network accessibility, indicating how dense the infrastructure is relative to people, and network coverage ,indicating how dense it is relative to land area on the distribution of consignment types. This dual approach provides a more complete understanding of how infrastructure characteristics shape freight transport behaviour across European countries.

This analysis tests whether different measures of network density population-based and area-based have a measurable effect on the distribution of consignment types across European countries. Therefore the following hypotheses will be tested:
H₀₁: Network population density has no significant influence on the distribution of consignment types.


H₁₁: Network population density significantly influences the distribution of consignment types.


H₀₂: Network area density has no significant influence on the distribution of consignment types.


H₁₂: Network area density significantly influences the distribution of consignment types.

**The results.**

A scatterplot was selected as the most appropriate visualization technique because it effectively represents the relationship between two continuous variables network density and consignment volume. This format allows for the clear identification of general patterns, such as positive or negative trends, while also visualizing the dispersion and variability of data points across countries and years.
The scatterplots in Figures 2.1 and 2.2 visualize the relationship between network density and the distribution of consignment types.

Figure 2.1
![network_pop_density_vs_consignments.png](attachment:network_pop_density_vs_consignments.png)

The scatterplot in Figure 2.1 illustrates the relationship between network population density and consignment distribution. The results show a negative trend, suggesting that as rail accessibility relative to population increases, the total volume of freight transport decreases. This pattern shows some valueable insights, the full_train distribution moves roughly along the same trend as the total freight moved. However full-wagon consignments seem to be more independent of the population density. A suggestion could be that densely populated countries, mix passenger and freight together as much as sparsely populated countries do. However since the total and full wagon consignment decrease, relatively, the share of full_wagon consignments increases for densely populated country.

Figure 2.2
![network_area_density_vs_consignments.png](attachment:network_area_density_vs_consignments.png)

In contrast, Figure 2.2 shows the relationship between network area density and consignment volume. Here, a positive association is observed countries with more spatially extensive rail networks tend to have higher total freight volumes and a greater proportion of full-train consignments. This implies a higher dependence of freight transport on the geographical coverage of the rail network. A denser spatial network supports long-distance, bulk, and industrial shipments, leading to a more uneven distribution of consignment types dominated by full-train loads. Relatively the share of full-wagon loads decreases, however the actual full-wagon loads moved seem to remain the same.

The creation of both images can be found in this [**notebook**](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Scripts/Sub-question-2/Sub_question_2.ipynb), manually it can be found : ../Scripts/Sub-question-2/Sub_question_2.ipynb.

**Hypotheses testing.**

To verify these observed relationships, a Chi-Squared Test of Independence was conducted to statistically assess whether the distribution of consignment types differs significantly across categories of network density. The results of these tests are discussed in the following section. 
The first test, based on network population density, yielded a Chi-Squared statistic of χ²(2, N = 124) = 6.08, with a corresponding p-value = 0.0479. Since this value is slightly below the 0.05 threshold, the null hypothesis (H₀₁) can be rejected. This indicates a weak but statistically significant dependency between network density relative to population and the distribution of consignment types. In practical terms, this suggests that in countries with denser rail networks per capita, the distribution of freight consignments differs systematically likely due to greater accessibility and diversified transport use between passenger and freight services.

The second test, using network area density, produced χ²(2, N = 117) = 4.72, with a p-value = 0.0947. Because this result exceeds the 0.05 significance level, H₀₂ cannot be rejected, meaning that no statistically significant dependency was detected between network density per land area and consignment type distribution. Although the scatterplot in Figure 2.2 suggested a positive relationship, the statistical evidence is insufficient to confirm that the two variables are dependent at the 95% confidence level.

The confidence testing of this sub-question can be found in this [**notebook**](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Scripts/Sub-question-2/Sub_question_2.ipynb), manually it can be found : ../Scripts/Sub-question-2/Sub_question_2.ipynb.

**Conclusion. #2**

The analysis demonstrates that network density influences freight distribution in  distinct ways depending on how it is measured. While spatial network coverage does also indicate significant affects to the composition of consignments, there is to little statistical evidence to support this claim. Therefore we can conclude that there is a weak statistical evidence that network density influences rail consignment, most likely due to accesability. Low accesible rail networks move more freight in comparison to more dense counterparts.

 It is important to note that some of the data points were obtained through interpolation and extrapolation using curve-fitting techniques, which introduces a degree of uncertainty into the analysis. Although standard deviations were included to quantify this uncertainty, these approximations may affect the precision of the statistical relationships.The calculated uncertainty values Is discussed in the chapter uncertainty.These findings suggest that rail network accessibility plays a subtle yet meaningful role in shaping freight behavior across Europe.


# 3 How does the network length influence the modal share? 

The code for this subquestion can be found [here](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Scripts/Sub-question-3/rico_sq.ipynb)

Several columns in the merged dataset were used to answer this sub research question. Namely: the rail network length in kilometers, modal share, total freight volume transported, population and the country area. Rail density was not in the merged dataset but was calculated by dividing the rail network length by country area, resulting in kilometers of track per square kilometer of land area. Besides the rail density over land, rail density by population was also calculated. The resulting variable is kilometers of track per person. The most recent year with information about modal share was 2023. This year was picked for all variables for consistency sake. The assumption is made that 2023 is still valid in 2025 because influences such as COVID and the Ukraine war are accounted for.

In the scatterplots below we see the relationship between a variety of different variables that were also presented above. The R² of these relationships will be noted after the plots

Figure 3.1 Scatterplot for relationships

![image.png](https://raw.githubusercontent.com/etyurkay/TIL6022-Group-Project/refs/heads/main/Charts/Sub-question-3/sq3_fig9.png)

![image.png](https://raw.githubusercontent.com/etyurkay/TIL6022-Group-Project/refs/heads/main/Charts/Sub-question-3/sq3_fig10.png)

![image.png](https://raw.githubusercontent.com/etyurkay/TIL6022-Group-Project/refs/heads/main/Charts/Sub-question-3/sq3_fig11.png)

![image.png](https://raw.githubusercontent.com/etyurkay/TIL6022-Group-Project/refs/heads/main/Charts/Sub-question-3/sq3_fig12.png)

![image.png](https://raw.githubusercontent.com/etyurkay/TIL6022-Group-Project/refs/heads/main/Charts/Sub-question-3/sq3_fig13.png)

![image.png](https://raw.githubusercontent.com/etyurkay/TIL6022-Group-Project/refs/heads/main/Charts/Sub-question-3/sq3_fig14.png)

The R² between the two variables is given in the table below

| Variable 1               | Variable 2             | R²     |
|---------------------------|------------------------|--------:|
| Network Length            | Modal Share            | 0.006  |
| Network Density Land      | Modal Share            | 0.003  |
| Network Density Population| Modal Share            | **0.534** |
| Network Length            | Total Freight          | **0.701** |
| Network Density Land      | Total Freight          | 0.211  |
| Network Density Population| Total Freight          | 0.007  |

We can see that for modal share the only correlated network characteristic is the network density per capita. The network length itself and length per land area have no correlation with modal share at all. An explanation for this is that population is an approximation for the size of the economy while the land area is not.The countries with a high network density by population have more infrastructure available for their economy. The countries with the highest network density by population in the EU are vast countries with a low population density such as Finland and Sweden. The spread of economic activities over a larger area makes rail transportation a more attractive option. Countries with a low rail density per capita tend to have a higher population density such as Italy, Belgium and The Netherlands. These countries have industrial areas more closely concentrated together making rail less effective than alternatives such as trucking. The Netherlands and Belgium additionally have dense waterway networks that compete with rail.

For the total freight volumes a higher network length does correlate fairly strongly with the total freight transported. In this case however the density by both land and population do not show a strong correlation. The total freight volumes and network length give an absolute value of the scale while the densities are relative.

The notebook used to answer this question can be found [**here**](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Scripts/Sub-question-3/rico_sq.ipynb), manually it can be found at: ../Scripts/Sub-question-3/rico_sq.ipynb.



# 4 How is rail freight activity distributed among EU countries, and which nations lead or lag in freight volume?


This section investigates the distribution of rail freight activity across European Union member states to answer the sub-question: “How is rail freight activity distributed among EU countries"? The analysis is based on processed Eurostat data containing information on rail freight volumes (measured in million tonne-kilometres) across multiple years.The primary objective is to identify patterns of freight dominance and disparity among member states and to explore whether certain countries consistently lead or lag in total rail transport activity. A series of visual analyses is employed to illustrate overall freight distribution, compare the top and bottom performers, and assess long-term trends and stability among leading nations.

**The Results**

**Top 10 EU Countries by Total Rail Freight(Million tonne-km)**

![image.png](attachment:image.png)

The chart illustrates the total volume of rail freight transported by the top ten EU countries. Germany clearly dominates with nearly 2 million million tonne-kilometres, reflecting its position as Europe’s industrial and logistical hub. Poland and France follow as major contributors, each handling a substantial share of EU rail freight due to their strong manufacturing sectors and well-connected rail corridors. The remaining countries in the top ten — including Sweden, Austria, Czechia, Latvia, Lithuania, Romania, and Switzerland — show moderate freight volumes that reflect their roles as key transit and regional freight partners.
Overall, the distribution reveals a high concentration of rail freight activity within a few large economies, suggesting that rail transport efficiency and investment are strongly linked to industrial output, geographic centrality, and established logistics infrastructure.


 **Top 5 and Bottom 5 EU Countries by Total Rail Freight**

![image.png](attachment:image.png)

Figure presents a direct comparison between the five highest and five lowest EU countries in total rail freight volume. The left panel again shows Germany, Poland, France, Sweden, and Austria as clear leaders, while the right panel highlights Denmark, Belgium, Greece, Luxembourg, and Ireland as the lowest performers. The gap between the two groups is striking — Germany’s freight volume exceeds that of the lowest five countries combined by a large margin.
This disparity reflects not only differences in economic scale and geographic reach but also variations in transport policy and infrastructure prioritization. Smaller countries and island nations like Luxembourg and Ireland rely more on road or maritime transport, whereas larger continental economies sustain more extensive freight rail operations. The visualization thus underscores how rail freight intensity varies sharply across Europe, influenced by national infrastructure capacity, industrial demand, and cross-border connectivity.


 **Freight trend over time of Top 5 EU Countries**

![image.png](attachment:image.png)

This figure displays the evolution of rail freight volumes from 2008 to 2024 for the five leading EU countries — Germany (DE), Poland (PL), France (FR), Sweden (SE), and Austria (AT). Across the observed period, Germany consistently remains the highest freight carrier, with volumes fluctuating slightly but maintaining an upward trend overall. This indicates the stability and resilience of its rail freight network, even during economic slowdowns and post-pandemic recovery phases.
Poland demonstrates a steady and positive growth trend, showing increasing freight activity, likely linked to its growing role as a logistics corridor between Eastern and Western Europe. France maintains moderate freight levels with mild fluctuations, suggesting stable but limited growth potential in its rail sector. Meanwhile, Austria and Sweden show relatively smaller but consistent volumes, reflecting their importance as regional freight and transit hubs within Central and Northern Europe.


**Hypothesis Testing  - Distribution of Rail Freight Across EU Countries**

![image-2.png](attachment:image-2.png)

This figure visualizes the total rail freight volumes across EU countries alongside an expected equal-share benchmark (red dashed line). The Chi-Square test was conducted to evaluate whether rail freight is uniformly distributed among EU member states or significantly concentrated in a few.

1) Null Hypothesis (H₀): Rail freight volume is equally distributed across EU countries.


2) Alternative Hypothesis (H₁): Rail freight volume is not equally distributed across EU countries.


The observed distribution shows that a few countries — particularly Germany, Poland, and France handle a disproportionately large share of rail freight compared to others, while several smaller nations contribute minimally. The Chi-Square statistic yielded a very high value with a near-zero p-value, leading to the rejection of the null hypothesis.
This result confirms that rail freight activity is highly uneven across Europe, dominated by a small number of countries with extensive infrastructure and industrial demand. The disparity highlights the concentration of freight operations in central and western Europe, reflecting both economic geography and the unequal development of rail networks across the EU.


**Conclusion**

The analysis of EU rail freight volumes provides a clear picture of uneven spatial distribution across member countries, reflecting deeper structural and infrastructural differences within Europe’s transport system. A small number of countries—most notably Germany, Poland, and France—carry the majority of the continent’s rail freight, supported by their strong industrial bases, strategic geographic locations, and highly developed railway networks. In contrast, smaller or peripheral nations handle limited freight volumes, often due to restricted network connectivity, smaller domestic markets, or greater reliance on maritime and road transport.

These disparities reveal that the railway network itself plays a decisive role in shaping freight patterns: countries with dense, cross-border rail corridors and intermodal hubs attract higher volumes and a broader diversity of commodity types. The significant statistical deviation found through the chi-square test further confirms that the current distribution is structurally concentrated rather than evenly spread.

In relation to the main research question, the findings indicate that infrastructure quality, economic geography, and industrial specialization jointly determine how rail freight is distributed by consignment and commodity

The notebook used to answer this question can be found [here](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Scripts/Sub-question-4/Sub_Question_4.ipynb), manually it can be found at: ../Scripts/Sub-question-4/Sub_Question_4.ipynb.


# 5 How do commodity groups (NST 2007 classification) influence the distribution of consignment types?


This section examines the correlation between the nature of the cargo and the choice of transport type (e.g., full train load vs. single-wagon load) in freight transport. Specifically, it aims to reveal whether cargo sent by train or by single wagon is prioritized for different commodity groups.
This analysis contributes to the main research question in the following ways from a broader perspective:
The main question seeks to answer “Which models dominate in rail logistics?” based on cargo types, transport type, and geographical distribution. Understanding which mode of transport is more efficient for the nature of the cargo (e.g., metal ore, chemicals, agricultural products, etc.) will also provide insight into how rail infrastructure and service models should be shaped. High-volume train services such as full-train loads or block trains, which carry goods from a single consignor to a single destination, are considered particularly suitable for bulk and primary raw materials. In contrast, single-wagonload services, where individual wagons from different customers are marshalled and combined into one train, are typically associated with smaller shipment sizes and more complex logistical connections (European Commission, 2015, p. 19).
Thus, revealing how different types of cargo are preferred in terms of transport mode provides a basis for policy implications in terms of infrastructure planning, network capacities, and logistics models. For example, if a group of goods is mostly transported by full train load, the railway company may need to consider forming train blocks, establishing fixed routes, and planning reverse logistics. Otherwise, if there are scattered shipments based on wagons, more maneuvering, sorting, and wagon management will be required at terminals which may affect efficiency. 
Briefly, this sub-question helps us understand the relationship between the type of cargo and the mode of transport, revealing which cargo groups are geared toward which transport models in rail freight and what this means in terms of infrastructure and logistics planning. 

**Data usage**

The data used in this analysis is based on commodity (based on cargo type according to the NST2007 classification) transport data and consignment (full train/full wagon) data.
Both data sets are based on Eurostat Rail Freight Statistics. However, their contents and the number of countries they cover are not exactly the same. When considering EU countries, the commodity dataset includes 25 countries, while the data containing consignment type shares includes only 12 countries. Therefore, the analysis only considers countries common to both datasets, excluding countries such as Belgium, where almost all data is missing. Ultimately, data from 11 countries was used, with gaps in some years filled using interpolation. Furthermore, prior to the analysis, rows with empty or zero values for both total transport volume and train and wagon share data were excluded as they would not contribute to the analysis.

**Analysis**

For this analysis, a heatmap and stacked bar chart were chosen for visualization. The heatmap helps to see the volume differences between commodities based on the freight type, while the stacked bar chart shows how the freight type preference is distributed based on the commodity. Lastly, the chi-square test was used to determine whether the commodity type and consignment type are independent from each other.

**Results**

The general analysis conducted at the EU level clearly shows general trends, such as the predominance of bulk cargo (e.g., coal, metal ores, petroleum products) being transported by rail, but it has also revealed some inconsistent results. For example, categories such as Grouped goods (mixed consignments) and Machinery and equipment have shown high rail freight rates, even though such goods would be expected to rely on more fragmented or flexible wagon-based logistics. 

![image-4.png](attachment:image-4.png)

![image.png](attachment:image.png)

First, it was thought that these inconsistencies might stem from data limitations rather than actual transport behavior. Missing values in the freight transport dataset, irregular time scope, and differences in national reporting practices between countries may have contributed to this. Another reason could be that, unlike traditional modes of transport, multimodal and intermodal transport are also used alongside traditional methods. However, this was not included as a separate category in the Eurostat data. Since these combined modes of transport were not recorded separately, it does not fully report wagon freight traffic or classify intermodal transport under rail freight categories.It is also reported that wagons loaded with intermodal transport units are sometimes part of single-wagon trains, but are generally transported by full trains between two intermodal terminals (European Commission, 2015, p. 20). Therefore, even in cases where intermodal transport was used, we considered that reporting could have been done as full-train. To support this view with our data, Slovenia, one of the countries with complete data, was examined.  

![image-2.png](attachment:image-2.png)

![image-3.png](attachment:image-3.png)

When we examined a country like Slovenia, which has complete data, we also found that the full-train share was higher for most commodity types. This reinforced our assumption and led us to conclude that the share of total train load may have been artificially exaggerated due to the lack of consistent wagon records.

However, despite these imbalances in the distribution, the hypothesis test yielded the expected results and revealed a dependency between commodity type and consignment type.

The notebook used to answer this question can be found [here](https://github.com/etyurkay/TIL6022-Group-Project/blob/main/Scripts/Sub-question-5/q5-analysis.ipynb), manually it can be found at: ../Scripts/Sub-question-5/q5-analysis.ipynb.


# Removed Question 
- How has the trend of full train consignments changed over time in the top and bottom-five EU freight countries?


The main reason for excluding this question from the scope was the significant lack of data in the consignment data. Our idea was to first find the top and bottom countries in rail freight in question 4 and then look at the trend in the countries listed with this output. However, as can be seen in question 1, the consignment data caused us to eliminate many countries with many missing data points, otherwise it would not have been possible to perform trend analysis or we would not have been able to obtain accurate results. Therefore, since the number of countries was already reduced to 7, looking at the top and bottom 5 countries became meaningless. Since we believed that all other questions contributed sufficiently to our main research question, we decided to remove this one.

# Conclusion

This study set out to answer the main research question:  
“How is rail freight distributed across European countries by consignment type and commodity group, and how does the railway network influence these patterns and trends?”

The analyses across multiple datasets and statistical tests show that rail freight distribution in Europe is highly uneven, strongly shaped by the interraction between: network infrastructure, industrial structure, and the types of goods transported. The results indicate that national economies, network accessibility, and commodity characteristics jointly determine how freight is organized and moved across the continent.

The findings from all sub-questions collectively demonstrate how rail freight patterns are influenced by both infrastructural and economic factors across Europe:

- **(1) Consignment type by country:** Countries exhibit statistically distinct preferences for full-train versus full-wagon consignments, reflecting their industrial composition and logistics scale.  
- **(2) Network density influence:** Population-based network density modestly affects consignment distribution, with accessibility playing a stronger role than geographic coverage.  
- **(3) Network length and modal share:** Longer and denser networks correlate with total freight capacity, but only density by population meaningfully predicts rail’s modal share.  
- **(4) Freight distribution among EU countries:** Freight activity is heavily concentrated in a few industrialized nations, confirming a structural imbalance across Europe.  
- **(5) Commodity group influence:** The type of goods transported dictates consignment choice. However most transportation relies on full-train.

In conclusion, Europe’s rail freight system is defined by the interaction between infrastructure accessibility, industrial specialization, and commodity characteristics. The railway network not only supports but actively shapes national freight behavior. To promote a more balanced and efficient freight system, European transport policy should prioritize enhancing network accessibility, improving data harmonization, and developing commodity-specific and intermodal infrastructure, ensuring that rail freight continues to evolve as a sustainable and competitive mode of transport across the continent.


# Contribution Statement

Each author is responsible for answering their own sub-question.

**Author 1**: 
Saumitra Deo

"How do different countries relate to different shares of consignment types?"

Tasks: Extract relevant Eurostat data from the merged file, Clean and preprocess country–consignment data, Build contingency tables (country vs. consignment type), Perform chi-square test of independence, Create visualizations: bar charts, heatmaps of shares by country, Write results section discussing differences across countries.

**Author 2**:
Youri Beijer

"How does network density influence consignment?"

Tasks: Create a network density variable(s), cross reference network density to consignment type, Perform correlation analysis  between network density and consignment types, Run regression models to test influence of network length, Create scatter plots with regression lines, Document methodology and statistical findings.

Additionally: Youri Beijer was responsible for data merging and cleaning.

Merging tasks: Download all relevant data sets for each sub-question, Merge them into one csv creating collumns filled with observation values, Index them on geoplotical entities and years, Filter relevant geoplotical entities (EU + CH).

Cleaning tasks: Evaluate data coverage, Evaluate whether data reported by geopolitical entites is useable. Curve-fit NaN values of consignment types using all present data, record uncertainties.

**Author 3**:
Rico de Jong

"How does the network length influence the modal share?"

Tasks: Extract data on modal share of rail freight from the merged file, Link modal share with network length & density indicators, Conduct regression analysis (network length & density vs. modal share), Create scatter plots, regression plots, and comparative tables, Interpret whether denser networks show higher modal shares, Draft results and add visual evidence to the report.

**Author 4**:
Pranshu Sharma

"How is rail freight activity distributed among EU countries and which nations lead or lag in freight volume?"

Tasks: Extract rail freight volume dataset from the merged file, Rank countries and identify top 5 and bottom 5, Compare structural differences (total volume, growth trends), Produce tables, rankings, and bar plots of volumes, Write results section interpreting patterns among high vs. low performers.

**Author 5**:
Ecem Tyurkay

"How has the trend of full train consignments changed over time in the top- and bottom-five EU freight countries?" (removed)

Tasks: Filter dataset for full train consignments, Perform time-series analysis (2008–present), Plot trends for top 5 and bottom 5 countries (line charts, percentage shares), Test hypotheses using regression or trend analysis.

"How do commodity groups (NST 2007 classification) influence the distribution of consignment types?"

Tasks: Retrieve dataset (rail_go_grpgood) from the merged file, Build contingency tables (commodity group × consignment type), Run chi-square independence tests, Visualize with stacked bar charts and heatmaps, Interpret which commodity groups are linked to certain consignment types.

# References

1. European Commission. (2015). Study on Single Wagonload Traffic in Europe – Challenges, Prospects and Policy Options. Directorate-General for Mobility and Transport.
https://transport.ec.europa.eu/system/files/2017-02/2015-07-swl-final-report.pdf

