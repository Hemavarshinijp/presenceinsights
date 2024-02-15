# presenceinsights
Presence-Insights-Data-Analytics
Project Overview:
Include a brief overview of the project, its goals, and the technologies/tools used.
This repository contains the code and resources for a data analytics project focused on leveraging Presence Insights for HR requirements. The project aims to provide valuable insights through data analysis and visualization, addressing specific HR needs.
This Dashboard contains multiple excel files with different months and different columns so it is difficult to merge it into one file
Using power query to solved this issue

## Table of Contents
1. [Introduction](#introduction)
2. [HR Requirements](#hr-requirements)
3. [Gathering and Transforming Data](#gathering-and-transforming-data)
4. [Creating Matrix using DAX](#creating-matrix-using-dax)
5. [Dashboarding](#dashboarding)

## Introduction
Describe the purpose and scope of the project. Explain how Presence Insights is utilized for HR analytics and the benefits it brings to the organization.

## HR Requirements
Highlight specific HR requirements that the project addresses. Discuss the importance of data analytics in meeting these requirements and improving HR processes.

## Gathering and Transforming Data
Provide details on the data sources used, along with scripts or notebooks for data collection and preprocessing. Explain the rationale behind data choices.

## Creating Matrix using DAX
Explain the significance of Data Analysis Expressions (DAX) in the project. Include DAX scripts or formulas used for creating matrices to analyze HR data.

## Dashboarding
Showcase the design and development of dashboards. Include code and visualization examples to illustrate how Presence Insights data is presented for HR decision-making.

## DAX used in this Dashboard
i) Total Working Days = 
var Totaldays = Count('Final Data'[Value])
var NonworkDays = CALCULATE(count('Final Data'[Value]), 'Final Data'[Value] in {"WO", "HO"})
RETURN
Totaldays - NonworkDays

ii) Present Days = 
var presentDays = CALCULATE(COUNT('Final Data'[Value]), 'Final Data'[Value]="p")
RETURN
presentDays + [WFH Count]

iii) WFH Count = SWITCH ( TRUE(),
'Final Data'[Value] = "WFH",1,
'Final Data'[Value] = "HWFH",0.5, 0 )

iv) WFH Count = sum('Final Data'[WFH Count])

v) SL Count = SWITCH ( TRUE(),
'Final Data'[Value] = "SL",1,
'Final Data'[Value] = "HSL",0.5, 0 )

vi) SL Count = SUM('Final Data'[SL Count])

vii) WFH % = DIVIDE([WFH Count], [Present Days],0)

viii) SL % = DIVIDE([SL Count], [Total Working Days],0)

ix) Day of week = FORMAT('Final Data'[Date], "ddd")




