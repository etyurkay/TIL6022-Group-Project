![][image1]

# 

# ---

# “Railway freight analysis, regarding consignment types, commodities vs network characteristics”

# ---

TIL 6020 Design challenge \- Research proposal

Youri Beijer (4965027)  
Ecem Tyurkay (6301207)  
Rico de Jong (5348870)  
Saumitra Deo (6434223)  
Pranshu Sharma (6505015)

October 3rd 2025

# Table of Contents {#table-of-contents}

[**Table of Contents	2**](#table-of-contents)

[**1\. Introduction	3**](#introduction)

[**2\. Research objectives & \-questions	4**](#research-objectives-&--questions)

[2.1 Research question	4](#2.1-research-question)

[2.2 Sub-questions	4](#2.2-sub-questions)

[**3\. Scope	6**](#scope)

[3.1 Defining scope	6](#3.1-defining-scope)

[3.1.1 Geographical scope	6](#3.1.1-geographical-scope)

[3.1.2 Temporal scope	6](#3.1.2-temporal-scope)

[3.1.3 Thematic scope	6](#3.1.3-thematic-scope)

[3.1.4 Analytical scope	7](#3.1.4-analytical-scope)

[3.2 Exclusions	7](#3.2-exclusions)

[3.3 Limitations	8](#3.3-limitations)

[**4\. Methodology	9**](#methodology)

[**4.1 Git-hub versioning (VS Code workflow)	9**](#4.1-git-hub-versioning-\(vs-code-workflow\))

[**4.2 Hypotheses testing	10**](#4.2-hypotheses-testing)

[**5\. Initial literature	11**](#initial-literature)

[**6\. Planning	12**](#planning)

[**Week 1 (05/10/2025 \-11/10/2025) :	12**](#week-1-\(05/10/2025--11/10/2025\)-:)

# 

1. # Introduction {#introduction}

In recent years, increasing attention has been directed toward shifting freight transport from road to rail. The transport sector accounts for around one-fifth of global CO₂ emissions, with road freight alone responsible for nearly 30% of these emissions (Ritchie, 2020). Reducing the environmental impact of road freight is therefore critical to lowering overall freight-related emissions. Rail offers a more sustainable option, emitting up to six times less CO₂ per tonne-kilometer than road transport (Department for Energy Security and Net Zero, 2020). Beyond environmental benefits, shifting freight to rail can also reduce road congestion in high-traffic areas. Given these advantages, it is important to understand the factors that influence rail freight usage in order to develop effective policies that encourage a greater modal shift toward rail.

Several factors may influence rail freight utilization across different countries. For instance, rail network length and density are likely to correlate positively with rail usage. The type of consignment (i.e. full or partial trains) may also play a role. To investigate these relationships, this study uses publicly available Eurostat data, which covers EU members as well as a few other European countries. This data not only allows for the analysis of known factors of rail freight usage but may also reveal additional hidden factors. By identifying network characteristics and consignment types of countries with high rail freight usage, lessons can be learned to guide improvements in countries where rail remains less well used.

This document is a project proposal for a more extensive report to be completed at a later stage. Following this introduction, Chapter 2 will present the research questions used in the study. Chapter 3 will define the scope of the project, while Chapter 4 will outline the initial methodology. Finally, the proposal concludes with a list of the literature used and the preliminary project planning.

2. # Research objectives & \-questions {#research-objectives-&--questions}

The purpose of this chapter is to outline the objectives of the study and to present the central research question alongside a set of sub-questions. These elements together provide direction for the research, ensuring that the analysis remains systematic, coherent, and aligned with the overall aim of the thesis.

## 2.1 Research question {#2.1-research-question}

The aim of this report is to answer the following research question:

***"How is rail freight distributed across European countries by consignment type and commodity group, and how does the railway network influence these patterns/trends?"***

## 2.2 Sub-questions {#2.2-sub-questions}

To address the main research question in a structured way, it is divided into several sub-questions, each focusing on a specific aspect of freight distribution, commodity and network influence. Hypotheses formed already regarding these sub-questions and statistical methods will be used to test validity of these questions.

* How do different countries relate to different shares of consignment types?  
  ***Hypothesis:***  
  *H0: There is **no significant relationship** between a country and the distribution of consignment types.*   
  *H1: There is a **significant relationship** between a country and the distribution of consignment types.*    
    
* How does network length influence consignment?   
  ***Hypotheses:***  
  *H0: Network length has no influence on the distribution of consignment types.*  
  *H1: Network length has a significant influence on the distribution of consignment types.*

* How does the network length influence the modal share?   
  ***Hypothesis***
  *H0: There is no correlation between network length and density and rail modal share*
  *H1: There is a positive correlation between network length and density and rail modal share. A larger, more dense network makes rail a more attractive option.*
  * The rail network length of a country might correlate with the modal share of rail freight usage.   
  * A distinction can be made between overall network length and network density (km of track per km² land area).  
  * Modal share and network length can be accessed from EuroStat.  
  * Data can be used to create a scatter plot of network length and modal share, a simple regression can be performed to see the relationship.

* Which 5 EU countries have the most train freight?  

* How has the trend of full train consignments changed over time in the top- and bottom-five EU freight countries?
  ***Hypotheses:***  
    *H0: There is no significant change in the share of full train consignments over time in the top 5 freight countries.*
    *H1: There is a significant increase in the share of full train consignments over time in the top 5 freight countries.*  
  * The bottom five countries will not be included in the hypothesis test. These countries will only be observed with charts to understand the trend.  
   
* How do commodity groups (NST 2007 classification) influence the distribution of consignment types?  
  ***Hypotheses:***  
  *H0: Commodity distribution and consignment type are independent.*  
  *H1: Commodity distribution and consignment type are not independent.*

# 

3. # Scope {#scope}

This chapter defines the boundaries of the research to ensure clarity and focus. It outlines the defining scopes of the study (geographical, temporal, thematic, and analytical), specifies key exclusions, addresses inherent limitations, and ends with a framing statement that explains how the study is bounded.

## 3.1 Defining scope {#3.1-defining-scope}

The research scope is divided into categories to make clear what is included in the study and how it aligns with the research objectives.

### 3.1.1 Geographical scope {#3.1.1-geographical-scope}

This thesis focuses on European Union member states, with emphasis on the five countries with the highest and the five countries with the lowest rail freight volumes (based on Eurostat data). This dual selection makes it possible to compare rail freight efficiency across countries where rail freight is dominant versus countries where it is minimal, thereby highlighting structural differences in distribution patterns and network influence.

### 3.1.2 Temporal scope {#3.1.2-temporal-scope}

The temporal frame extends from 2008 onwards, aligning with the availability of harmonized Eurostat datasets under the NST 2007 commodity classification. Data prior to this period are excluded due to inconsistencies in classification and reporting standards.

### 3.1.3 Thematic scope {#3.1.3-thematic-scope}

The study is restricted to rail freight consignments, commodity groups, and railway network characteristics. These dimensions are chosen as they represent measurable determinants of rail freight efficiency.

### 

### 3.1.4 Analytical scope {#3.1.4-analytical-scope}

The analysis is designed to investigate how rail freight is distributed across countries and how the railway network influences these patterns and trends. Each component of the research question is linked directly to datasets and methods:

* **Distribution of freight by consignment type and commodity group**  
   *Datasets:* rail\_go\_consgmt, rail\_go\_grpgood.  
   *Method:* Descriptive statistics and comparative analysis of top 5 vs. bottom 5 countries.

* **Trends in consignment distribution over time**  
   *Dataset:* rail\_go\_consgmt.  
   *Method:* Time-series analysis (2008–present), focusing on changes in full train vs. wagonload consignments.

* **Relationship between commodity groups and consignment types**  
   *Datasets:* rail\_go\_grpgood, rail\_go\_consgmt.  
   *Method:* Contingency tables, chi-square tests for independence, supported by visualizations such as stacked bar charts and heatmaps.

* **Influence of railway network characteristics**  
   *Dataset:* rail\_if\_line\_na.  
   *Method:* Correlation and regression analysis comparing network length and electrification against distributional patterns.

We will go more in depth on the methods in chapter 4, where we will extensively analyze our workflow and testing methods.

## 3.2 Exclusions {#3.2-exclusions}

To maintain a clear and focused analysis, several aspects are excluded from this study:

* **Passenger transport:** The analysis is restricted to rail freight only. Passenger rail services, as well as combined passenger–freight operations, are not considered.

* **Non-European networks:** The study focuses exclusively on EU member states.

* **Other freight transport modes:** Road, air, and maritime freight are excluded except where briefly mentioned for contextual comparison.

* **Forecasting and predictive modeling:** The study does not attempt to predict future freight flows or infrastructure development. Instead, it focuses solely on observed historical data.

* **Operator-level detail:** The analysis is conducted at a country–year level using Eurostat data. Company-level logistics, terminal performance, and operational strategies are excluded due to data unavailability.

## 3.3 Limitations {#3.3-limitations}

* **Comparability across countries:** Differences in infrastructure, reporting standards, and national railway policies may introduce inconsistencies, limiting the precision of cross-country comparisons between top- and bottom-performing states.

* **Time coverage:** The analysis begins in 2008 to align with the NST 2007 classification. Trends before this period cannot be examined, which may exclude potentially relevant historical developments.  
    
* **Focus on distributional patterns:** The study emphasizes consignment type, commodity group, and network characteristics. Other factors influencing freight patterns—such as policy measures, economic shocks, or logistics strategies—are acknowledged but not included in the analysis.

* **Infrastructure indicators:** Network length and electrification are used as proxies for infrastructure quality. These indicators do not capture more complex aspects of network performance, such as capacity utilization, bottlenecks, or service reliability.

4. # Methodology  {#methodology}

This chapter defines the following methods to be applied to establish a standard working discipline during coding throughout the project and to test the validity of research questions (hypotheses).

# 4.1 Git-hub versioning (VS Code workflow) {#4.1-git-hub-versioning-(vs-code-workflow)}

To avoid any confusion or errors in the later stages of the project, each team member will follow the same standardized workflow. 

1. **Update the main branch**  
- At the beginning of each work session, the  **“main”** branch will be updated by opening the Source Control panel in VS Code (the Git icon on the left). At the bottom of the window, the current branch will be displayed as “**main”**  
- The **“Sync Changes”** button (two arrows) will be clicked to pull the latest updates from GitHub, ensuring that the local version is up to date.


2. **Create a new branch for your task**  
- A new branch will be created by clicking the branch name (main) in the lower-left corner of VS Code and selecting *“Create new branch”*.  
- A descriptive name will be given (e.g., **q5/full-train-trend**). This will allow the work to be carried out separately from the stable main branch.


3. **Write and test your code**  
- The assigned code will be implemented in notebooks or scripts, and the necessary tests (e.g., **pytest**) will be run to confirm that the implementation works as expected

4. **Commit your changes**  
- The Source Control panel will show the modified files. The relevant files will be staged, and a clear commit message will be written (e.g., *“feat: add trend plot for full train consignments”*). The commit will then be confirmed by clicking the checkmark icon.


5. **Push your branch to GitHub**  
- After committing, VS Code will suggest “Publish Branch” or “Sync Changes.” By selecting this option, the branch will be uploaded to GitHub and made available to the team.


6. **Open a Pull Request (PR)**  
- A Pull Request will be opened either through the GitHub Pull Requests extension in VS Code or directly on GitHub by using the *“Compare & Pull Request”* button. A short description of the changes will be provided, and a reviewer will be assigned.


  

7. **Review and merge**  
- Each Pull Request will be reviewed by at least one team member. Once approved and confirmed, it will be merged into the main branch. After merging, the feature branch will be deleted to keep the repository clean.


8. **Conflict Management**  
- If a conflict occurs, it will be shown in VS Code with clear markers. The team member will open the file in the Merge Editor and choose whether to keep their own version, the incoming version, or combine both. This decision will be given according to the simplified rule set below.  
  - If both changes are in *different parts of the file*: both versions will be kept (combined).  
  - If the same line is changed in two different ways:  
    - The version that matches the **latest state of the dataset or analysis** will be chosen.  
    - If both changes are needed, they will be **manually combined** into one line.  
  - If the decision is unclear: the team will discuss it shortly and agree on the correct version before committing.

# 4.2 Hypotheses testing {#4.2-hypotheses-testing}

For statistical analysis, a hypothesis test will be applied to each sub-question. The hypotheses defined in Chapter 2 will be tested using the chi-square method.  
Chi-square method (χ² test):

1. A contingency table (rows \= commodity groups, columns \= consignment types) will be created or the two data sets will be combined.  
2. A chi-square test will be performed for each sub-question using **scipy.stats.chi2\_contingency**.  
3. The p-value will be interpreted as follows:  
- If **p ≥ 0.05** → H0 cannot be rejected (there is no significant relationship).  
- If **p \< 0.05** → H0 is rejected (there is a significant relationship).

Additionally, different statistical calculations can be included (such as correlation, regression, ANOVA etc.).

5. # Initial literature {#initial-literature}

   

   1\.      Department for Energy Security and Net Zero. (2020, 17 July). Greenhouse gas reporting: conversion factors 2020\. [GOV.UK](http://gov.uk).[https://www.gov.uk/government/publications/greenhouse-gas-reporting-conversion-factors-2020](https://www.gov.uk/government/publications/greenhouse-gas-reporting-conversion-factors-2020)  
   2\.      Ritchie, H. (2020, 6 October). Cars, planes, trains: where do CO₂ emissions from transport come from? Our World in Data. [https://ourworldindata.org/co2-emissions-from-transport](https://ourworldindata.org/co2-emissions-from-transport)  
   3\.      Goods transported by type of consignment-.   [https://ec.europa.eu/eurostat/databrowser/view/rail\_go\_consgmt/default/table?lang=en\&category=rail.rail\_go](https://ec.europa.eu/eurostat/databrowser/view/rail_go_consgmt/default/table?lang=en&category=rail.rail_go)  
   4\.      Length of electric and non-electric railway lines by nature of transport [https://ec.europa.eu/eurostat/databrowser/view/rail\_if\_line\_na/default/table?lang=en\&category=rail.rail\_i](https://ec.europa.eu/eurostat/databrowser/view/rail_if_line_na/default/table?lang=en&category=rail.rail_i)  (To filter the data, freight only will be selected under the “Traffic and transport measurement” category.)  
   5\.     Goods transported by group of goods \- from 2008 onwards based on NST 2007 (rail\_go\_grpgood) [https://ec.europa.eu/eurostat/databrowser/view/rail\_go\_grpgood/default/table?lang=en\&category=rail.rail\_go](https://ec.europa.eu/eurostat/databrowser/view/rail_go_grpgood/default/table?lang=en&category=rail.rail_go)

   

6. # Planning {#planning}

# **Week 1** (05/10/2025 \-11/10/2025) **:** {#week-1-(05/10/2025--11/10/2025)-:}

* Data Collection from various sources  
* Cleaning and pre-processing the data  
* Repository and environmental setup  
* Beginning initial visualizations

**Week 2** (12/10/2025-18/10/2025) **:**

* Data Cleanup and pre-processing of data  
* Hypothesis Testing   
* Data Visualizations   
* Beginning the report writing

**Week 3** (19/10/2025-25/10/2025) **:**

* Refining of the visualizations   
* Report Refinement and finalization  
* Documentation completion

**Important Dates:**  
19/10/2025- Mid-term check up of project

[image1]: <data:image/png;base64,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S3aIJGIisdxYo0aN1OjRo/WAysm4BLxAi3LChAmqVatWepBInkMsg9Bdd911avjw4XH55cIukrjOgwYN8m1pS6NI5jLw4qbWrVsHtj59+sgicoQTmRUVXeHRSzapF+dsUo99uV21nLZVNZ2UpteZ9JpJg7RG47eophPTVMupaerRL9NVj292qpGLNuqyjmGeYjaAhwqrfstrF49h3nWXLl1U//799cgxXtqVlpaW5cLoBQYgpk+frr8DQorwtkN0n9GKhZjhL/yNaHViwAaj2hBW+C5xjvGC9S7l90eITbxlLVq0yFUOriP8hScLRB8/TnXr1tWRBpiZhGvgvCa4RrgmuBa5iTwvkqnMniMn1Jxth9TI1fvUO8v2qLeXZqgh3/9umf8Pz0z7aNVe9fXWQyrjSNZ0pfMic+fOVT179tRdaAjnY489pud9v/baa2r58uUye64H8aNoWT777LPq8ccf19cEweXdunVT/fr148ANIYTkJSiShBBigSJJCCEWKJKEEGKBIkkIIRYokoQQYoEiSQghFiiShBBigSJJCCEWKJKEEGKBIkkIIRYokoQQYoEiSQghFiiShBBigSJJCCEWKJKEEGKBIkkIIRYokoQQYoEiSQghFiiShBBigSJJCCEWKJKEEGKBIkkIIRYokoQQYoEiSQghFiiShBBigSJJCCEWKJKEEGKBIkkIIRYokoQQYoEiSQghFiiShBBigSJJCCEWKJKEEGKBIkkIIRYokoQQYoEiSQghFiiShBBigSJJCCEWKJKEEGKBIkkIIRYokoQQYoEiSQghFiiShBBigSJJCCEWKJKEEGKBIkkIIRYokoQQYoEiSQghFiiShBBigSJJCCEWki6Sx48fVxs3bvS1vXv3yl0S4pdfflETJ05U69evl5vUr7/+qjZs2KDee+899cwzz6iPP/5YZvHF7/wPHjwYlU9uh8XLgQMH1Isvvqg2b94sN4WGcePGqSFDhsjkUIB7NXr0aNW9e3c1aNAglZ6eLrPo+ybvk83kfc4Kvv/++6RdQ9tzkldJukgeOnRIDRs2TD366KOe9vLLL6tRo0apHTt2yF0DM2PGDNWrVy9VuHBhNX78eLlZzZs3T7Vr1049+OCDqlChQuqcc84JfLzDhw9rcXWe8+uvv67S0tKi8n344YdRebBPvCxdulTly5dPDRw4UG4KDZdddpk6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>