---
title: "green_blue_analysis"
author: "Daniel Fuller"
date: "12/05/2022"
output:
  html_document:
    keep_md: true
---



## Analysis of Green Blue Data


```r
green_blue <- read_csv("Data Extraction PHAC Built Environment_2022_05_16.csv")
```

```
## New names:
## * `` -> ...27
```

```
## Rows: 62 Columns: 27
```

```
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (24): first_author_last_name, city, country, study_design, intervention,...
## dbl  (3): year, comparison_sample, comparison_sample1
```

```
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
green_blue$measure <- str_trim(green_blue$measure)

green_blue$'type of measure' <- str_trim(green_blue$'type of measure')

table(green_blue$metric)
```

```
## 
##                                     bikeability 
##                                               3 
##                                     Green Space 
##                                              20 
##      Green Space (also appeared in Walkability) 
##                                               1 
##                       Green Space & Walkability 
##                                               1 
##                                     walkability 
##                                              18 
##                                     Walkability 
##                                              11 
## Walkability (and built enironment more broadly) 
##                                               1 
##                     walkability and bikeability 
##                                               5 
##           Walkability; Green Space (park audit) 
##                                               1 
##                        walkbility & bikeability 
##                                               1
```

```r
green_blue <- filter(green_blue, metric == "Green Space")
```

## List and count of types of measures


```r
table(green_blue$'type of measure')
```

```
## 
##              audit parent self-report        self-report 
##                 14                  1                  4
```

```r
table(green_blue$measure)
```

```
## 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           “Is there a public park or play park within 10 min walk of here [your residence]?” Those who reported “Yes” were considered to have access to a local park, while those reporting “No” were not. 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      “Please tell me if the following places and things are available to your children in your neighborhood, even if [CHILD'S NAME] does not actually use them: 1) A park or playground area; and 2) A recreation center, community center, or boys’ or girls’ club”. Parents self-reported whether a park, playground area, recreation centre, community centre, or boys’/girls’ club was available in the neighbourhood. 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         Are there good parks and playgrounds/play spaces?” 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Community Park Audit Tool (CPAT) 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          2 
## For the green space attributes, participants were asked whether green space access (e.g., walking distance and road system), type (e.g., green space in residential areas and multifunctional parks) or size (e.g., 1, 2 and 5 Ha) played a role in respondents’ health promotion. The landscape characteristics were measured by asking whether plants (e.g., ornamental features and canopy density), water (e.g., artificial and natural), sensory features (e.g., sound and smell) or microclimate environments (e.g., temperature and humidity) contributed to health promotion. The facilities were assessed by asking respondents whether rest facilities (e.g., seats and pergolas with chairs) or amenity facilities (e.g., exercise facilities, running paths, swings and slides) had an impact on their health promotion. All the response options were listed on a Likert scale (1 = strongly disagree to 5 = strongly agree). 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Observational Park Audit Tool (OPAT) 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          PARK (Parks, Activity, and Recreation among Kids) 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           Parks and Play Spaces Direct Observation (PPSDO) tool and SOPARC 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Public Open Space Audit Tool (POST) 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Public Open Space Tool. 32 out of the 49 items from POST. We excluded items that were absent \n(e.g., barbecue area, dog fountains) and/or present (e.g., presence \ntrees, access to public transport) in all green spaces, as they did not \ndiscriminate green spaces, and items with an unpredictable impact in \ngreen space use (e.g., arrangement of paths and trees). 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Question: There are good parks, playgrounds and play spaces in this neighborhood. Response options: strongly agreed, agreed, disagreed, or strongly disagreed. 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Respondents’ assessment of whether there are good parks or playgrounds in the neighborhood and whether respondents feel comfortable going to the park or playground closest to where she lives during the day. Both indicators are coded on a 4-point scale with higher levels indicating higher agreement. 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   SOPARC (or modified versions, such as SOPLAY or SOPARNA) 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          1 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           System for Observing Play and Recreation in Communities (SOPARC) 
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          6
```

Overal there were 16 measures using audit based tools, 1 measure using parent self-report and 4 measures using self-report. 

The data for the measures is a bit messier. There were a number of instances of studies using SOPARC or self-report in combination with other audit based measures, which is why the numbers don't sum to 16.  

## Audit based tools
* 9 = System for Observing Parks and Recreation in Communities (SOPARC)
* 1 = Community Park Audit Tool (CPAT)
* 1 = Observational Park Audit Tool (OPAT)
- 1 = Stanford Neighborhood Discovery Tool 
- 2 = Public Open Space Audit Tool (POST)
- 1 = Parks, Activity, and Recreation among Kids (PARK) 
- 1 = Parks and Play Spaces Direct Observation (PPSDO)
- 1 = System for Observing Play and Leisure Activity in Youth (SOPLAY) 
- 1 = System for Observing Physical Activity and Recreation in Natural Areas (SOPARNA)

## Self-report tools

The majority of self-report tools were based on similar questions about park access by distance or time. This could be from the parent (in one case) or the child (in 4 cases). 

1. “Please tell me if the following places and things are available to your children in your neighborhood, even if [CHILD'S NAME] does not actually use them: 
    * A park or playground area
    * A recreation center, community center, or boys’ or girls’ club”. 
    * Parents self-reported whether a park, playground area, recreation centre, community centre, or boys’/girls’ club was available in the neighbourhood. 
2. “Is there a public park or play park within 10 min walk of here [your residence]?” 
    * Those who reported “Yes” were considered to have access to a local park, while those reporting “No” were not. 
3. Are there good parks and playgrounds/play spaces?” 
4. For the green space attributes, participants were asked whether green space access (e.g., walking distance and road system), type (e.g., green space in residential areas and multifunctional parks) or size (e.g., 1, 2 and 5 Ha) played a role in respondents’ health promotion. 
    * The landscape characteristics were measured by asking whether plants (e.g., ornamental features and canopy density), water (e.g., artificial and natural), sensory features (e.g., sound and smell) or microclimate environments (e.g., temperature and humidity) contributed to health promotion. The facilities were assessed by asking respondents whether rest facilities (e.g., seats and pergolas with chairs) or amenity facilities (e.g., exercise facilities, running paths, swings and slides) had an impact on their health promotion. 
    * All the response options were listed on a Likert scale (1 = strongly disagree to 5 = strongly agree). 
5. There are good parks, playgrounds and play spaces in this neighborhood. Response options: strongly agreed, agreed, disagreed, or strongly disagreed. 
6. Respondents’ assessment of whether there are good parks or playgrounds in the neighborhood and whether respondents feel comfortable going to the park or playground closest to where she lives during the day. 
    * Both indicators are coded on a 4-point scale with higher levels indicating higher agreement. 
