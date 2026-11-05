**Date:** October 29, 2026<br>
**Course:** MPAD 2003 A - Introductory Data Storytelling<br>
**Student Name:** Tessa Roberts (#101371137)<br>
**Presented to:** Jean-Sébastien Marier<br>
<br>

# Deliverable 2: Exploratory Data Analysis (EDA)

<!--Use one hashtag symbol (`#`) to create a level 1 heading like this one.

## Foreword

For this assignment, you must clean and analyze the dataset from Deliverable 1, create exploratory charts/visualizations, and identify a potential story. Your assignment must clearly detail your process. You are expected to write about 1,000-1,200 words, and to include several screen captures showing the different steps you went through. Your assignment must be written with the Markdown format and submitted on GitHub.

I have been assigning different versions of this project to my digital journalism and data storytelling students for a few years now. Its structure was inspired by the main sections/chapters of [*The Data Journalism Handbook*](https://datajournalism.com/read/handbook/one/). This version was further inspired by the [Key Capabilities in Data Science](https://extendedlearning.ubc.ca/programs/key-capabilities-data-science) program offered by the University of British Columbia (UBC).

**Here are some useful resources for this assignment:**

* [GitHub's *Basic writing and formatting syntax* page](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
* [The template repository for this assignment in case you delete something by mistake](https://github.com/jsmarier/jou4100_jou4500_mpad2003_project2_template)

Did you notice how to create a hyperlink? In Markdown, we put the clickable text between square brackets and the actual URL between parentheses.

And to create an unordered list, we simply put a star (`*`) before each item. -->

## 1. Getting Data

The selected Dataset is the City of Ottawa's Database about <ins>[Public Washrooms](https://open.ottawa.ca/datasets/ottawa::public-washrooms/about).</ins>

**IMPORT INTO GOOGLE SHEETS:** 

**1.** Click "<ins>Download</ins>", select the CVS file option, then "<ins>Save</ins>".
![](downloading-database-step1.jpg)
*Figure 1: Downloading database from Open Ottawa.*

**2.** Open Google Sheets, Click "<ins>File</ins>", then "<ins>Import</ins>", then "<ins>Upload</ins>" to import the CSV file.
![](downloading-database-step2.1.jpg)
*Figure 2: CSV file import on Google Sheets.*

![](downloading-database-step2.2.jpg)
*Figure 3: Google Sheets "Import data" file prompt.*

**3.** Click "<ins>Import data</ins>" and now the file has been imported!
![](downloading-database-imported.jpg)
*Figure 4: First 28 rows of fully imported Database.*

**Public GoogleSheets Link:** <ins> https://docs.google.com/spreadsheets/d/1WWs_5XDITIMu7ZMi5Y0k4jcVvdXTl-t2ZMsUHL9qOp0/edit?usp=sharing </ins>

**Dataset Observations:**
The dataset appears consistent across 52 columns and 180 rows. Information starts off dense towards the left and gradually gets more spaced out the farther the columns reach the right, where most data is duplicated to adapt French translations. However the final 2 rows and columns are completely empty. 

The data features both Right and Left text alignments; with numerical data being aligned right as shown for the (-X, Y) coordinates in columns A-B and washroom opening and closing hours in columns M-AF. Meanwhile, all nominal data is aligned left like in column D for location names or column AO for their Jurisdiction.
Interestingly, the dataset features another set of (-X, Y) coordinates in columns AM-AN. Both seemingly pinpoint the washroom locations, bringing up the question of why a second coordinate system is needed when location information is already provided in columns A-B.

While specified information helps to differentiate data types, duplicate information makes it hard to navigate and coupled with the mixed alignments, information can appear overly cluttered at first glance.



<!--<br> Use two hashtag symbols (`##`) to create a level 2 heading like this one.

To include a screen capture, use the sample code below. Your images should be saved in the same folder as your `.md` file.

![](import-screen-capture.png)<br>
*Figure 1: The "Import file" prompt on Google Sheets.*

**Here are examples of functions and lines of code put in grey boxes:**

1. If you name a function, put it between "angled" quotation marks like this: `IMPORTHTML`.
1. If you want to include the entire line of code, do the same thing, albeit with your entire code: `=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)`.
1. Alternatively, you can put your code in an independent box using the template below:

``` r
=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)
```
This also shows how to create an ordered list. Simply put `1.` before each item. -->

## 2. Understanding Data

### 2.1. VIMO Analysis

<!-- Use three hashtag symbols (`###`) to create a level 3 heading like this one. Please follow this template when it comes to level 1 and level 2 headings. However, you can use level 3 headings as you see fit.-->

A VIMO analysis is an acronym representing different methods to assess the quality of data; Valid, Invalid, Missing or an Outlier (Government of Canada, 2020). Using these methods, I can analyze the quality of my chosen dataset on Ottawa’s Public Washrooms.

**Column D - NAME**
<ins>VALID</ins>
Column D seems valid due to each facility name clearly defining the location as a park, centre, library or other public facility. The column contains 163 unique names, compared to a total of 5 duplicate names erach appearing with a frequency of 2 or 3 times. Most entries listed represent actual locations rather than repetitive or placeholder text.

<ins>INVALID</ins>
Row 52 has inconsistent naming convention for Mooney’s Bay by omitting the apostrophe in “Mooneys Bay Beach Building”.
While there are a handful of rows with identical names, it doesn’t mean they’re errors upon further inspection. Some duplicates have separate coordinates, implying they’re individual toilets within the same location. Meanwhile some share the same cell and pair of coordinates, but it’s unclear whether they reflect multiple toilets at one location, a duplicate text entry, or a unique formatting choice.

<ins>MISSING</ins>
No values appear to be missing. While there are 2 empty cells in rows 179 and 180, they appear to be part of the spreadsheet formatting and not meant to represent missing data.

<ins>OUTLIERS</ins>
Most duplicates are separated by 27-32 rows, meanwhile Claudette Cain Park and Deevy Pines Park deviate from the pattern of a large gap by respectively having close placements of 3 rows between, and none at all.
<br>
**Column F - FACILITY_GROUP_NAMES**
<ins>VALID</ins>
Of the 179 toilet locations listed, 123 were tagged using 6 facility-group names: RECREATION, ARTS and CULTURES, CIVIC ADMINISTRATIONS, PROTECTIVE SERVICES, SOCIAL SERVICES, and GENERAL PURPOSE. The consistent naming and format of those names displays a standard category system.

<ins>INVALID</ins>
No values have been found invalid. All cells that are not empty follow the 6 facility group names standardized in the dataset.

<ins>MISSING</ins>
There are a total of 56 empty cells within Column F. The final rows, 179 and 180, are completely empty and may have contributed to the calculation. All empty cells before are likely missing values since later the facility group names are specified. 

<ins>OUTLIERS</ins>
RECREATION, ARTS and CULTURE, and CIVIC ADMINISTRATION locations range from 10-73, making up the majority of the facility group names listed. In contrast, PROTECTIVE SERVICES, SOCIAL SERVICES and GENERAL PURPOSE are the outliers ranging between 1-3 of the locations listed.
<br>
**Column J, K, L - SEASONAL, SEASON_START, SEASON_END**
<ins>VALID</ins>
The data in Column J follows a binary system of 0 and 1. There are 108 rows containing 0 compared to the 69 rows containing 1. Each value correlates with the months marking the start (K) and end (L) time they’re open. Every value of 1 has seasonal month conditions, and every 0 has conditions marked with “NA”.

<ins>INVALID</ins>
No values have been found invalid. The data in columns K and L follow a consistent format of all capitalized letters in the month abbreviations and non-applicable (NA) seasonal conditions.

<ins>MISSING</ins>
No values appear to be missing. While there are 2 empty cells in rows 179 and 180, they appear to be part of the spreadsheet formatting and not meant to represent missing data.

<ins>OUTLIERS</ins>
No data outliers have been found, aside from the formatting issue that extends the length of the cells in row 57. Otherwise, all values follow the expected format.


<!--Support your claims by citing relevant sources. Please follow [APA guidelines for in-text citations](https://apastyle.apa.org/style-grammar-guidelines/citations).-->

**For example:**

As seen in Bounegru & Gray (2011), a data visualization should be clear...

### 2.2. Cleaning Data

Insert text here.

### 2.3. Analyzing Data

Insert text here.

**This section should include a screen capture of your pivot table, like so:**

![](pivot-table-screen-capture.png)<br>
*Figure 2: This pivot table shows...*

**This section should also include a screen capture of your exploratory chart, like so:**

![](chart-screen-capture.png)<br>
*Figure 3: This exploratory chart shows...*

## 3. Delivering Data

Insert text here.

## 4. References

Include a list of your references here. Please follow [APA](https://apastyle.apa.org/style-grammar-guidelines/references) or [MLA](https://www.mla.org/MLA-Style) guidelines for references. Hanging paragraphs aren't required though.

**Here's an example:**

Bounegru, L., & Gray, J. (Eds.). (2021). *The Data Journalism Handbook 2: Towards A Critical Data Practice*. Amsterdam University Press. [https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153](https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153)
