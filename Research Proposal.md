![](media/image1.png){width="4.569444444444445in"
height="2.8194444444444446in"}

#

# ---

# "Railway freight analysis, regarding consignment types, commodities vs network characteristics"

# 

TIL 6020 Design challenge - Research proposal

Youri Beijer (4965027)  
Ecem Tyurkay (6301207)  
Rico de Jong (5348870)  
Saumitra Deo (6434223)  
Pranshu Sharma (6505015)

October 3rd 2025

# Table of Contents

[**Table of Contents 2**](#table-of-contents)

[**1. Introduction 3**](#introduction)

[**2. Research objectives & -questions
4**](#research-objectives-&--questions)

[2.1 Research question 4](#research-question)

[2.2 Sub-questions 4](#sub-questions)

[**3. Scope 6**](#scope)

[3.1 Defining scope 6](#defining-scope)

[3.1.1 Geographical scope 6](#geographical-scope)

[3.1.2 Temporal scope 6](#temporal-scope)

[3.1.3 Thematic scope 6](#thematic-scope)

[3.1.4 Analytical scope 7](#analytical-scope)

[3.2 Exclusions 7](#exclusions)

[3.3 Limitations 8](#limitations)

[**4. Methodology 9**](#methodology)

[**4.1 Git-hub versioning (VS Code workflow)
9**](#X5dc87e3f6b1808422465ee11015a020dfb953d3)

[**4.2 Hypotheses testing 10**](#hypotheses-testing)

[**5. Initial literature 11**](#initial-literature)

[**6. Planning 12**](#planning)

[**Week 1 (05/10/2025 -11/10/2025) :
12**](#week-1-(05/10/2025--11/10/2025)-:)

#

# Introduction

In recent years, increasing attention has been directed toward shifting
freight transport from road to rail. The transport sector accounts for
around one-fifth of global CO₂ emissions, with road freight alone
responsible for nearly 30% of these emissions (Ritchie, 2020). Reducing
the environmental impact of road freight is therefore critical to
lowering overall freight-related emissions. Rail offers a more
sustainable option, emitting up to six times less CO₂ per
tonne-kilometer than road transport (Department for Energy Security and
Net Zero, 2020). Beyond environmental benefits, shifting freight to rail
can also reduce road congestion in high-traffic areas. Given these
advantages, it is important to understand the factors that influence
rail freight usage in order to develop effective policies that encourage
a greater modal shift toward rail.

Several factors may influence rail freight utilization across different
countries. For instance, rail network length and density are likely to
correlate positively with rail usage. The type of consignment (i.e. full
or partial trains) may also play a role. To investigate these
relationships, this study uses publicly available Eurostat data, which
covers EU members as well as a few other European countries. This data
not only allows for the analysis of known factors of rail freight usage
but may also reveal additional hidden factors. By identifying network
characteristics and consignment types of countries with high rail
freight usage, lessons can be learned to guide improvements in countries
where rail remains less well used.

This document is a project proposal for a more extensive report to be
completed at a later stage. Following this introduction, Chapter 2 will
present the research questions used in the study. Chapter 3 will define
the scope of the project, while Chapter 4 will outline the initial
methodology. Finally, the proposal concludes with a list of the
literature used and the preliminary project planning.

# Research objectives & -questions

The purpose of this chapter is to outline the objectives of the study
and to present the central research question alongside a set of
sub-questions. These elements together provide direction for the
research, ensuring that the analysis remains systematic, coherent, and
aligned with the overall aim of the thesis.

## 2.1 Research question

The aim of this report is to answer the following research question:

***"How is rail freight distributed across European countries by
consignment type and commodity group, and how does the railway network
influence these patterns/trends?"***

## 2.2 Sub-questions

To address the main research question in a structured way, it is divided
into several sub-questions, each focusing on a specific aspect of
freight distribution, commodity and network influence. Hypotheses formed
already regarding these sub-questions and statistical methods will be
used to test validity of these questions.

- How do different countries relate to different shares of consignment
  types?  
  ***Hypothesis:***  
  *H0: There is **no significant relationship** between a country and
  the distribution of consignment types.*  
  *H1: There is a **significant relationship** between a country and the
  distribution of consignment types.*

- How does network length influence consignment?  
  ***Hypothesis:***  
  *H0: Network length has no influence on the distribution of
  consignment types.*  
  *H1: Network length has a significant influence on the distribution of
  consignment types.*

- How does the network length influence the modal share?  
  ***Hypothesis***  
  *H0: There is no correlation between network length and density and
  rail modal share.* *H1: There is a positive correlation between
  network length and density and rail modal share. A larger, more dense
  network makes rail a more attractive option.*

  - The rail network length of a country might correlate with the modal
    share of rail freight usage.
  - A distinction can be made between overall network length and network
    density (km of track per km² land area).
  - Modal share and network length can be accessed from EuroStat.
  - Data can be used to create a scatter plot of network length and
    modal share, a simple regression can be performed to see the
    relationship.

- Which 5 EU countries have the most train freight?

- How has the trend of full train consignments changed over time in the
  top- and bottom-five EU freight countries?  
  ***Hypothesis:***  
  *H0: There is no significant change in the share of full train
  consignments over time in the top 5 freight countries.*  
  *H1: There is a significant increase in the share of full train
  consignments over time in the top 5 freight countries.*

  - The bottom five countries will not be included in the hypothesis
    test. These countries will only be observed with charts to
    understand the trend.

- How do commodity groups (NST 2007 classification) influence the
  distribution of consignment types?  
  ***Hypothesis:***  
  *H0: Commodity distribution and consignment type are independent.*  
  *H1: Commodity distribution and consignment type are not independent.*

#

# Scope

This chapter defines the boundaries of the research to ensure clarity
and focus. It outlines the defining scopes of the study (geographical,
temporal, thematic, and analytical), specifies key exclusions, addresses
inherent limitations, and ends with a framing statement that explains
how the study is bounded.

## 3.1 Defining scope 

The research scope is divided into categories to make clear what is
included in the study and how it aligns with the research objectives.

### 3.1.1 Geographical scope 

This thesis focuses on European Union member states, with emphasis on
the five countries with the highest and the five countries with the
lowest rail freight volumes (based on Eurostat data). This dual
selection makes it possible to compare rail freight efficiency across
countries where rail freight is dominant versus countries where it is
minimal, thereby highlighting structural differences in distribution
patterns and network influence.

### 3.1.2 Temporal scope 

The temporal frame extends from 2008 onwards, aligning with the
availability of harmonized Eurostat datasets under the NST 2007
commodity classification. Data prior to this period are excluded due to
inconsistencies in classification and reporting standards.

### 3.1.3 Thematic scope 

The study is restricted to rail freight consignments, commodity groups,
and railway network characteristics. These dimensions are chosen as they
represent measurable determinants of rail freight efficiency.

###  

### 3.1.4 Analytical scope 

The analysis is designed to investigate how rail freight is distributed
across countries and how the railway network influences these patterns
and trends. Each component of the research question is linked directly
to datasets and methods:

- **Distribution of freight by consignment type and commodity group**  
  *Datasets:* rail_go_consgmt, rail_go_grpgood.  
  *Method:* Descriptive statistics and comparative analysis of top 5
  vs. bottom 5 countries.

- **Trends in consignment distribution over time**  
  *Dataset:* rail_go_consgmt.  
  *Method:* Time-series analysis (2008--present), focusing on changes in
  full train vs. wagonload consignments.

- **Relationship between commodity groups and consignment types**  
  *Datasets:* rail_go_grpgood, rail_go_consgmt.  
  *Method:* Contingency tables, chi-square tests for independence,
  supported by visualizations such as stacked bar charts and heatmaps.

- **Influence of railway network characteristics**  
  *Dataset:* rail_if_line_na.  
  *Method:* Correlation and regression analysis comparing network length
  and electrification against distributional patterns.

We will go more in depth on the methods in chapter 4, where we will
extensively analyze our workflow and testing methods.

## 3.2 Exclusions

To maintain a clear and focused analysis, several aspects are excluded
from this study:

- **Passenger transport:** The analysis is restricted to rail freight
  only. Passenger rail services, as well as combined passenger--freight
  operations, are not considered.

- **Non-European networks:** The study focuses exclusively on EU member
  states.

- **Other freight transport modes:** Road, air, and maritime freight are
  excluded except where briefly mentioned for contextual comparison.

- **Forecasting and predictive modeling:** The study does not attempt to
  predict future freight flows or infrastructure development. Instead,
  it focuses solely on observed historical data.

- **Operator-level detail:** The analysis is conducted at a
  country--year level using Eurostat data. Company-level logistics,
  terminal performance, and operational strategies are excluded due to
  data unavailability.

## 3.3 Limitations 

- **Comparability across countries:** Differences in infrastructure,
  reporting standards, and national railway policies may introduce
  inconsistencies, limiting the precision of cross-country comparisons
  between top- and bottom-performing states.

- **Time coverage:** The analysis begins in 2008 to align with the NST
  2007 classification. Trends before this period cannot be examined,
  which may exclude potentially relevant historical developments.

- **Focus on distributional patterns:** The study emphasizes consignment
  type, commodity group, and network characteristics. Other factors
  influencing freight patterns---such as policy measures, economic
  shocks, or logistics strategies---are acknowledged but not included in
  the analysis.

- **Infrastructure indicators:** Network length and electrification are
  used as proxies for infrastructure quality. These indicators do not
  capture more complex aspects of network performance, such as capacity
  utilization, bottlenecks, or service reliability.

# Methodology

This chapter defines the following methods to be applied to establish a
standard working discipline during coding throughout the project and to
test the validity of research questions (hypotheses).

# 4.1 Git-hub versioning (VS Code workflow) 

To avoid any confusion or errors in the later stages of the project,
each team member will follow the same standardized workflow.

1.  **Update the main branch**

- At the beginning of each work session, the **"main"** branch will be
  updated by opening the Source Control panel in VS Code (the Git icon
  on the left). At the bottom of the window, the current branch will be
  displayed as "**main"**
- The **"Sync Changes"** button (two arrows) will be clicked to pull the
  latest updates from GitHub, ensuring that the local version is up to
  date.

2.  **Create a new branch for your task**

- A new branch will be created by clicking the branch name (main) in the
  lower-left corner of VS Code and selecting *"Create new branch"*.
- A descriptive name will be given (e.g., **q5/full-train-trend**). This
  will allow the work to be carried out separately from the stable main
  branch.

3.  **Write and test your code**

- The assigned code will be implemented in notebooks or scripts, and the
  necessary tests (e.g., **pytest**) will be run to confirm that the
  implementation works as expected

4.  **Commit your changes**

- The Source Control panel will show the modified files. The relevant
  files will be staged, and a clear commit message will be written
  (e.g., *"feat: add trend plot for full train consignments"*). The
  commit will then be confirmed by clicking the checkmark icon.

5.  **Push your branch to GitHub**

- After committing, VS Code will suggest "Publish Branch" or "Sync
  Changes." By selecting this option, the branch will be uploaded to
  GitHub and made available to the team.

6.  **Open a Pull Request (PR)**

- A Pull Request will be opened either through the GitHub Pull Requests
  extension in VS Code or directly on GitHub by using the *"Compare &
  Pull Request"* button. A short description of the changes will be
  provided, and a reviewer will be assigned.

7.  **Review and merge**

- Each Pull Request will be reviewed by at least one team member. Once
  approved and confirmed, it will be merged into the main branch. After
  merging, the feature branch will be deleted to keep the repository
  clean.

8.  **Conflict Management**

- If a conflict occurs, it will be shown in VS Code with clear markers.
  The team member will open the file in the Merge Editor and choose
  whether to keep their own version, the incoming version, or combine
  both. This decision will be given according to the simplified rule set
  below.
  - If both changes are in *different parts of the file*: both versions
    will be kept (combined).
  - If the same line is changed in two different ways:
    - The version that matches the **latest state of the dataset or
      analysis** will be chosen.
    - If both changes are needed, they will be **manually combined**
      into one line.
  - If the decision is unclear: the team will discuss it shortly and
    agree on the correct version before committing.

# 4.2 Hypotheses testing 

For statistical analysis, a hypothesis test will be applied to each
sub-question. The hypotheses defined in Chapter 2 will be tested using
the chi-square method.  
Chi-square method (χ² test):

1.  A contingency table (rows = commodity groups, columns = consignment
    types) will be created or the two data sets will be combined.
2.  A chi-square test will be performed for each sub-question using
    **scipy.stats.chi2_contingency**.
3.  The p-value will be interpreted as follows:

- If **p ≥ 0.05** → H0 cannot be rejected (there is no significant
  relationship).
- If **p \< 0.05** → H0 is rejected (there is a significant
  relationship).

Additionally, different statistical calculations can be included (such
as correlation, regression, ANOVA etc.).

# Initial literature

- 1\. Department for Energy Security and Net Zero. (2020, 17 July).
  Greenhouse gas reporting: conversion factors 2020.
  [GOV.UK](http://gov.uk).<https://www.gov.uk/government/publications/greenhouse-gas-reporting-conversion-factors-2020>  
  2. Ritchie, H. (2020, 6 October). Cars, planes, trains: where do CO₂
  emissions from transport come from? Our World in Data.
  <https://ourworldindata.org/co2-emissions-from-transport>  
  3. Goods transported by type of consignment-.
  <https://ec.europa.eu/eurostat/databrowser/view/rail_go_consgmt/default/table?lang=en&category=rail.rail_go>  
  4. Length of electric and non-electric railway lines by nature of
  transport
  <https://ec.europa.eu/eurostat/databrowser/view/rail_if_line_na/default/table?lang=en&category=rail.rail_i>
  (To filter the data, freight only will be selected under the "Traffic
  and transport measurement" category.)  
  5. Goods transported by group of goods - from 2008 onwards based on
  NST 2007 (rail_go_grpgood)
  <https://ec.europa.eu/eurostat/databrowser/view/rail_go_grpgood/default/table?lang=en&category=rail.rail_go>

# Planning

# Week 1 (05/10/2025 -11/10/2025) :

- Data Collection from various sources
- Cleaning and pre-processing the data
- Repository and environmental setup
- Beginning initial visualizations

**Week 2** (12/10/2025-18/10/2025) **:**

- Data Cleanup and pre-processing of data
- Hypothesis Testing
- Data Visualizations
- Beginning the report writing

**Week 3** (19/10/2025-25/10/2025) **:**

- Refining of the visualizations
- Report Refinement and finalization
- Documentation completion

**Important Dates:**  
19/10/2025- Mid-term check up of project
