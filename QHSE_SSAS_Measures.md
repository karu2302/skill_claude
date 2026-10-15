# QHSE SSAS Measure Expressions

Source artifact: `TEMP SSAS bim model/QHSE/QHSE.bim`
Model id: `SemanticModel`
Source branch: SSAS `main`, latest as of 2026-10-13 per user; source commit was not supplied.
Source SHA-256: `658e5fe3425325cd10264bbeef3f8b42f370419606d6b717abbe7faf5be65553`
Measures extracted: `67`

This file contains the model's DAX measure names and expressions only. It does not include data-source definitions, connection strings, credentials, or deployment settings. Use the expressions as evidence: a column dependency is direct only when that column is referenced in an expression. A measure-to-measure dependency is supported only when an expression references that measure. Do not infer dependency from table membership or measure names alone.

## ACT Target

Model table: `Measure`

```dax
 [Total number actions] * "0.8 "
```
## ACTION %

Model table: `Measure`

```dax
  [Total number timely closed actions]/([Total number actions]*0.8)
```
## CSRD_MT Own Workforce

Model table: `Measure`

```dax
VAR RWCOwnWorkforce = CALCULATE( DISTINCTCOUNT(Incident[Process URL Id]), FILTER( 'Incident IP', 'Incident IP'[Classification Injury]="Restricted Work" && CONTAINSSTRING('Incident IP'[Employee Categorization],"Own Workforce") && 'Incident IP'[LTI Type Worldwide] <>"Disapproved" ), FILTER( 'Incident', 'Incident'[Commuting Related Incident] =FALSE() && 'Incident'[Non Work Related Incident] =FALSE() ) ) RETURN IF(ISBLANK(RWCOwnWorkforce),0,RWCOwnWorkforce)
```
## CSRD_RWC Own Workforce

Model table: `Measure`

```dax
VAR RWCOwnWorkforce = CALCULATE( DISTINCTCOUNT(Incident[Process URL Id]), FILTER( 'Incident IP', 'Incident IP'[Classification Injury]="Restricted Work" && CONTAINSSTRING('Incident IP'[Employee Categorization],"Own Workforce") && 'Incident IP'[LTI Type Worldwide] <>"Disapproved" ), FILTER( 'Incident', 'Incident'[Commuting Related Incident] =FALSE() && 'Incident'[Non Work Related Incident] =FALSE() ) ) RETURN IF(ISBLANK(RWCOwnWorkforce),0,RWCOwnWorkforce)
```
## DWH_ACT_TotalDEME_Result

Model table: `Measure`

```dax
 CALCULATE(     DISTINCTCOUNT('Action'[Process URL Id]),      'Action'[Status Performance] = "in time",      FILTER(         'Action',         'Action'[Source Name] IN {             "Incident",             "Investigation",             "External audit",             "Internal audit",             "supplier / subcontractor audit",             "Audit",             "action plan"         }         ||         'Action'[Plan Category Description] = "QHSE-S year action plan"         ||         'Action'[Event Type Of Meeting] = "management review meeting"     ) )
```
## DWH_CheckEntity_Active

Model table: `Measure`

```dax
 SUMX(     ADDCOLUMNS(         SUMMARIZE(             POVO,             POVO[POVO Id],             POVO[POVO Type],             POVO[POVO Start Date],             POVO[POVO End Date]         ),         "Active",             INT(                 POVO[POVO Type] = "Entity"                 && POVO[POVO Start Date] <= MAX('Overall Date'[DateTime])                 && POVO[POVO End Date] = DATE(9999,1,1)             )     ),     [Active] )
```
## DWH_CheckOS_Active

Model table: `Measure`

```dax
 SUMX(     ADDCOLUMNS(         SUMMARIZE(             POVO,             POVO[POVO Id],             POVO[POVO Type],             POVO[POVO Start Date],             POVO[POVO End Date]         ),         "Active",             IF(                 POVO[POVO Type] = "Other site"                     && POVO[POVO Start Date] <= MAX('Overall Date'[DateTime])                     && POVO[POVO End Date] = DATE(9999,1,1),                 1,                 0             )     ),     [Active] )
```
## DWH_CheckProject_Active

Model table: `Measure`

```dax
 SUMX(     ADDCOLUMNS(         SUMMARIZE(             POVO,             POVO[POVO Id],             POVO[POVO Type],             POVO[POVO Start Date],             POVO[POVO End Date]         ),         "Active",             IF(                 POVO[POVO Type] = "Project"                     && POVO[POVO Start Date] <= MAX('Overall Date'[DateTime])                     && POVO[POVO End Date] > MIN('Overall Date'[DateTime]),                 1,                 0             )     ),     [Active] )
```
## DWH_CheckVessel_Active

Model table: `Measure`

```dax
 SUMX(     ADDCOLUMNS(         SUMMARIZE(             POVO,             POVO[POVO Id],             POVO[POVO Type],             POVO[POVO Start Date],             POVO[POVO End Date]         ),         "Active",             IF(                 POVO[POVO Type] = "Vessel"                     && POVO[POVO Start Date] <= MAX('Overall Date'[DateTime])                     && POVO[POVO End Date] = DATE(9999,1,1),                 1,                 0             )     ),     [Active] )
```
## DWH_GI_Target

Model table: `Measure`

```dax
  SUMX(    SUMMARIZE(        filter(            POVO,            POVO[GI Required] =True &&            [DWH_CheckProject_Active] =1         ),        POVO[POVO Id Name],        "SumTarget",rounddown(divide(min([DWH_GI_TargetEnd],max('Overall Date'[DateTime])) -[DWH_GI_TargetStart] +1,365),0)     ),    [SumTarget] )
```
## DWH_GI_TargetEnd

Model table: `Measure`

```dax
 VAR DateStart = [DWH_GI_TargetStart] VAR DateEnd =     MAX ( POVO[GI Target End Date] ) RETURN     IF (         NOT ISBLANK ( DateStart ),         MIN ( DateEnd, TODAY() + 1 )     )
```
## DWH_GI_TargetStart

Model table: `Measure`

```dax
 VAR DateStart =     MIN ( POVO[GI Target Start Date] ) RETURN     IF (         DateStart = DATE ( 1900, 1, 1 ),         BLANK (),         DateStart     )
```
## DWH_INSP_TotalDEME_Result

Model table: `Measure`

```dax
 VAR INSP =     CALCULATE(         COUNT('Inspection Function'[Inspector Function]),          FILTER(             'Inspection Function',             'Inspection Function'[Inspector Function] IN {                 "Chief engineer",                 "project manager",                 "works manager",                 "superintendent",                 "Docking Team leader",                 "Technical superintendent",                 "master",                 "Project engineer",                 "Project director"             }         ),          FILTER(             POVO,             NOT(CONTAINSSTRING(POVO[POVO Exclude], "inspection"))             &&             (                 [DWH_CheckProject_Active] = 1                 || [DWH_CheckEntity_Active] = 1                 || [DWH_CheckVessel_Active] = 1                 || [DWH_CheckOS_Active] = 1             )         )     )  VAR NCVI =     CALCULATE(         DISTINCTCOUNT(Inspection[Process URL Id]),         FILTER(             Inspection,             CONTAINSSTRING(                 Inspection[Custom Inspection Id],                 "NCVI"             )         )     )  RETURN     INSP + NCVI
```
## DWH_OBS_TotalDEME_Result

Model table: `Measure`

```dax
 Var Project1 =calculate(DISTINCTCOUNT(Observation[Process URL Id]), filter(POVO,        [DWH_CheckProject_Active]=1&&            not(CONTAINSSTRING(POVO[POVO Exclude],"qhses-observation"     ) )))  Var Seahorse =calculate(DISTINCTCOUNT(Observation[Process URL Id]), filter(POVO,        POVO[POVO Id Name] ="d395 - Seahorse 1"             ) )  Var Rollingstone =calculate(DISTINCTCOUNT(Observation[Process URL Id]), filter(POVO,        POVO[POVO Id Name] ="d393 - Rollingstone"             ) )  Var Flintstone =calculate(DISTINCTCOUNT(Observation[Process URL Id]), filter(POVO,        POVO[POVO Id Name] ="d396 - Flintstone"             ) )  Return project1+Seahorse+Rollingstone+Flintstone 
```
## DWH_TBX_TotalDEME_Result

Model table: `Measure`

```dax
 CALCULATE(     SUM(Event[Total Participants]),     FILTER(         POVO,         NOT(CONTAINSSTRING(POVO[POVO Exclude], "event"))         &&         (             [DWH_CheckProject_Active] = 1             ||             POVO[POVO Id Name] = "D395 - Seahorse 1"             ||             POVO[POVO Id Name] = "d393 - Rollingstone"             ||             POVO[POVO Id Name] = "D396 - Flintstone"         )     ),      Event[Event Type] IN {         "Toolbox",         "Pre-work Meeting",         "Vessel-Project safety meeting",         "Safety moment day",         "Meeting",         "Campaign"     } )
```
## DWH_WH_DEME Project KPI

Model table: `Measure`

```dax
 CALCULATE(     SUM('Working Hour'[Number Of Employee Hours]) +     SUM('Working Hour'[Number Of Temporary Hours]) +     SUM('Working Hour'[Number Of Subcontractor Hours]) +     SUM('Working Hour'[Number Of Joint Venture Hours]),     FILTER(         POVO,         (             POVO[POVO Type] = "Project"                 && [DWH_CheckProject_Active]= 1                 && NOT(                     CONTAINSSTRING(                         POVO[POVO Exclude],                         "Event"                     )                 )         )         ||         POVO[POVO Id Name] IN {             "d396 - Flintstone",             "d393 - Rollingstone",             "d395 - Seahorse 1"         }     ) )
```
## DWH_WH_Total Working Hours DEME - Project KPI_obs

Model table: `Measure`

```dax
 VAR ProjectHours =     CALCULATE(         SUM('Working Hour'[Number Of Employee Hours]) +         SUM('Working Hour'[Number Of Temporary Hours]) +         SUM('Working Hour'[Number Of Subcontractor Hours]) +         SUM('Working Hour'[Number Of Joint Venture Hours]),          FILTER(             POVO,             POVO[POVO Type] = "Project"                 && [DWH_CheckProject_Active] = 1                 && NOT(                     CONTAINSSTRING(                         POVO[POVO Exclude],                         "qhses-observation"                     )                 )         )     )  VAR VesselHours =     CALCULATE(         SUM('Working Hour'[Number Of Employee Hours]) +         SUM('Working Hour'[Number Of Temporary Hours]) +         SUM('Working Hour'[Number Of Subcontractor Hours]) +         SUM('Working Hour'[Number Of Joint Venture Hours]),          FILTER(             POVO,             POVO[POVO Id Name] IN {                 "D396 - Flintstone",                 "D393 - Rollingstone",                 "D395 - Seahorse 1"             }         )     )  RETURN     ProjectHours + VesselHours
```
## INC APP

Model table: `Measure`

```dax
CALCULATE(DISTINCTCOUNT(Incident[Process URL Id]))
```
## INC Target

Model table: `Measure`

```dax
[Total Number Incidents]*0.9
```
## INC_MajorIncidentsEnvironmental

Model table: `Measure`

```dax
VAR EHIPO = CALCULATE( DISTINCTCOUNT(Incident[Process URL Id]), FILTER( 'Incident', Incident[E-Incident Red] ="E-HIPO-HICO" ) ) RETURN IF(ISBLANK(EHIPO),0,EHIPO)
```
## INC_MajorIncidentsHIPO

Model table: `Measure`

```dax
VAR HIPO = CALCULATE( COUNT(INCIDENT[Process URL Id]), FILTER( Incident, Incident[HIPO]=TRUE() ) ) RETURN IF(ISBLANK(HIPO),0,HIPO)
```
## INC_RedIncidentsEnvironmental

Model table: `Measure`

```dax
VAR EHIPORED = CALCULATE( DISTINCTCOUNT(INCIDENT[Process URL Id]), FILTER( 'Incident', CONTAINSSTRING(Incident[E-Incident Red],"red") ) ) RETURN IF(ISBLANK(EHIPORED),0,EHIPORED)
```
## INC_RedIncidentsHICO

Model table: `Measure`

```dax
VAR Variable = CALCULATE( DISTINCTCOUNT(Incident[Process URL Id]), FILTER( Incident, CONTAINSSTRING(Incident[Hico DEME],"hico cat 4") || CONTAINSSTRING(Incident[Hico DEME],"hico cat 5") || CONTAINSSTRING(Incident[Hico DEME],"hico cat 6") ) ) RETURN IF(ISBLANK(Variable),0,Variable)
```
## INC_RedIncidentsHIPO

Model table: `Measure`

```dax
VAR HIPORed = CALCULATE( DISTINCTCOUNT(INCIDENT[Process URL Id]), FILTER( Incident, Incident[hipo]=TRUE && Incident[Potential Risk Score 2]>15 ) ) RETURN IF(ISBLANK(HIPORed),0,HIPORed)
```
## INC_RedIncidentsLTI

Model table: `Measure`

```dax
VAR WWLTIOwnWorkforce = CALCULATE( DISTINCTCOUNT(Incident[Process URL Id]), FILTER( 'Incident IP', 'Incident IP'[Classification Injury]="Lost Time Incident" && CONTAINSSTRING('Incident IP'[Employee Categorization],"Own Workforce") && 'Incident IP'[LTI Type Worldwide] <>"Disapproved" && 'Incident IP'[Worldwide Equivalent] =TRUE() ), FILTER( 'Incident', 'Incident'[Commuting Related Incident] =FALSE() && 'Incident'[Non Work Related Incident] =FALSE() ) ) RETURN IF(ISBLANK(WWLTIOwnWorkforce),0,WWLTIOwnWorkforce)
```
## INC_RedIncidentsTotal

Model table: `Measure`

```dax
VAR Result = CALCULATE( DISTINCTCOUNT(Incident[Process URL Id]), FILTER( Incident, Incident[Red Incidents]=TRUE() ) ) RETURN IF(ISBLANK(Result),0,Result)
```
## INC_TotalNumberIncident

Model table: `Measure`

```dax
VAR Result = CALCULATE( DISTINCTCOUNT(Incident[Process URL Id]) ) RETURN IF(ISBLANK(Result),"-",Result)
```
## INS %

Model table: `Measure`

```dax
 DIVIDE([Total number inspections],[Total number PSD])
```
## Inspection %

Model table: `Measure`

```dax
[Total Number Inspections]/[Total Number PSD]
```
## INV Target

Model table: `Measure`

```dax
[Total Number IV Required]*0.85
```
## KPI Action

Model table: `Measure`

```dax
 [Total number timely closed actions] / [Total Number Actions]
```
## KPI OBS

Model table: `Measure`

```dax
 [Total Number Observations]*100000/[Total Working Hours - Project]
```
## KPI TBX

Model table: `Measure`

```dax
[Total Number Attendees]*100000/[Total Working Hours - Project]
```
## NC

Model table: `Measure`

```dax
SUM('Audit'[NC])
```
## Number of Incidents per Third Party Involved

Model table: `Measure`

```dax
COUNT('Incident Party Involved'[FactIncidentId])
```
## Number Of LT Injured Persons

Model table: `Measure`

```dax
  VAR _FirstDate = FirstDate('Date Unlinked'[DateTime]) VAR _LastDate = LASTDATE('Date Unlinked' [DateTime]) RETURN  SUMX(     ADDCOLUMNS(         VALUES('Date Unlinked'[DimDateId]),         "Days",                  CALCULATE ( VAR selecteddate = max('Date Unlinked'[DimDateId]) RETURN                     COUNTROWS(FILTER('Incident IP',selecteddate>='Incident IP'[DimDateStartLT] && selecteddate<='Incident IP'[DimDateEndLT]))                 )     ), [Days] ) + 0 
```
## Number Of RW Injured Persons

Model table: `Measure`

```dax
  VAR _FirstDate = FirstDate('Date Unlinked'[DateTime]) VAR _LastDate = LASTDATE('Date Unlinked' [DateTime]) RETURN  SUMX(     ADDCOLUMNS(         VALUES('Date Unlinked'[DimDateId]),         "Days",                  CALCULATE ( VAR selecteddate = max('Date Unlinked'[DimDateId]) RETURN                     COUNTROWS(FILTER('Incident IP',selecteddate>='Incident IP'[DimDateStartRW] && selecteddate<='Incident IP'[DimDateEndRW]))                 )     ), [Days] ) + 0
```
## OBS %

Model table: `Measure`

```dax
 [KPI OBS] / 75
```
## OBS Target

Model table: `Measure`

```dax
 INT(75*[Total Working Hours - Project]/100000)
```
## TBX %

Model table: `Measure`

```dax
[Total Number Attendees]*100000/[Total Working Hours - Project]/1200
```
## TBX Target

Model table: `Measure`

```dax
INT(1200*[Total Working Hours - Project]/100000)
```
## Thermometer

Model table: `Measure`

```dax
[Total Number WW]*200000/[Total Working Hours DEME]
```
## Time Diff

Model table: `Measure`

```dax
DATEDIFF(MIN(Incident[Incident Occured Date Time]),MIN(Incident[Incident Reported Date Time]),HOUR)
```
## Timely Reported INC %

Model table: `Measure`

```dax
[Total Number Timely Reported]/([Total Number Incidents]*0.9)
```
## Total Number Actions

Model table: `Measure`

```dax
  COUNTX(FILTER('Action', 'Action'[Source Name] IN {"Incident" ,"Investigation", "External audit", "Internal audit" ,"supplier / subcontractor audit"} || 'Action'[Plan Category Description] =  "QHSE-S year action plan" || 'Action'[Event Type] = "management review meeting"), 'Action'[Process URL Id])    
```
## Total Number Attendees

Model table: `Measure`

```dax
 CALCULATE(SUM(Event[Total Participants]),FILTER(Event,Event[Event Type]="Toolbox"||Event[Event Type]="Pre-work Meeting"||Event[Event Type]="Vessel-Project safety meeting"||Event[Event Type]="Safety moment day"))     
```
## Total Number Incidents

Model table: `Measure`

```dax
CALCULATE(DISTINCTCOUNT(Incident[Process URL Id]),FILTER(incident,Incident[Process Type]="Incident with damage"||Incident[Process Type]="Near-miss" ||Incident[Process Type]="Dangerous situation"))
```
## Total Number Inspections

Model table: `Measure`

```dax
CALCULATE(COUNT('Inspection Function'[Inspector Function]),FILTER('Inspection Function','Inspection Function'[Inspector Function]="Chief engineer"||'Inspection Function'[Inspector Function]="Master"||'Inspection Function'[Inspector Function]="Project Director"||'Inspection Function'[Inspector Function]="Project Manager"||'Inspection Function'[Inspector Function]="Works Manager"||'Inspection Function'[Inspector Function]="Superintendent"))
```
## Total Number Investigations

Model table: `Measure`

```dax
CALCULATE(DISTINCTCOUNT(Incident[Process URL Id]),FILTER(Incident,INCIDENT[Potential Risk Score]="2 - amber"||INCIDENT[Potential Risk Score]="3 - red"),FILTER(Incident,Incident[Investigation]=TRUE))
```
## Total Number IV Required

Model table: `Measure`

```dax
 CALCULATE(DISTINCTCOUNT(Incident[Process URL Id]),FILTER(Incident,INCIDENT[Potential Risk Score]="2 - amber"||INCIDENT[Potential Risk Score]="3 - red"))
```
## Total Number Observations

Model table: `Measure`

```dax
 DISTINCTCOUNT(OBSERVATION[Custom Observation Id])
```
## Total Number of Action Audits

Model table: `Measure`

```dax
DISTINCTCOUNT('Action Audit'[Action Id])
```
## Total Number of Actions per Finding

Model table: `Measure`

```dax
 SUM('Audit Finding'[NumberOfActions])
```
## Total Number of Audit Deficiencies

Model table: `Measure`

```dax
DISTINCTCOUNT('Audit Deficiency'[Deficiency Id])
```
## Total Number of Audit Findings

Model table: `Measure`

```dax
DISTINCTCOUNT('Audit Finding'[Finding Id])
```
## Total Number of Audits

Model table: `Measure`

```dax
DISTINCTCOUNT('Audit'[FactAuditId])
```
## Total Number PSD

Model table: `Measure`

```dax
SUMX('POVO Specific Data','POVO Specific Data'[Number Of Master And Chief Engineer]*4 					 + 'POVO Specific Data'[Number Of Superintendent Up To Project Director])
```
## Total Number Timely Closed Actions

Model table: `Measure`

```dax
 COUNTX(FILTER('Action', ('Action'[Source Name] IN {"Incident" ,"Investigation", "External audit", "Internal audit" ,"supplier / subcontractor audit"}  || 'Action'[Plan Category Description] =  "QHSE-S year action plan" || 'Action'[Event Type] = "management review meeting" ) && 'Action'[Status Performance] = "in time" ), 'Action'[Process URL Id])    
```
## Total Number Timely Reported

Model table: `Measure`

```dax
 CALCULATE(DISTINCTCOUNT(INCIDENT[Custom Incident ID]),FILTER(INCIDENT,[Time Diff] <=24))
```
## Total Number WW

Model table: `Measure`

```dax
 CALCULATE(DISTINCTCOUNT(INCIDENT[Process URL Id]),FILTER('Incident IP','Incident IP'[Worldwide Equivalent]=TRUE))
```
## Total Working Hours

Model table: `Measure`

```dax
 SUMX('Working Hour',  'Working Hour'[Number Of Employee Hours]                                          		      + 'Working Hour'[Number Of Joint Venture Hours]                                          		      + 'Working Hour'[Number Of Subcontractor Hours]                                          		      + 'Working Hour'[Number Of Temporary Hours]                                                 )
```
## Total Working Hours - Entity

Model table: `Measure`

```dax
 SUMX(FILTER('Working Hour', 'Working Hour'[DimEntityId]<>-1),      'Working Hour'[Number Of Employee Hours]                                                    				+ 'Working Hour'[Number Of Joint Venture Hours]                                                    				+ 'Working Hour'[Number Of Subcontractor Hours]                                                    				+ 'Working Hour'[Number Of Temporary Hours])
```
## Total Working Hours - Filtered

Model table: `Measure`

```dax
  VAR SelectedValues = VALUES('Type Of Working Hour'[Type Of Working Hour]) RETURN     SWITCH (         TRUE (),         SELECTEDVALUE('Type Of Working Hour'[Type Of Working Hour]) = "Employee", SUM('Working Hour'[Number Of Employee Hours]),         SELECTEDVALUE('Type Of Working Hour'[Type Of Working Hour]) = "Temporary", SUM('Working Hour'[Number Of Temporary Hours]),         SELECTEDVALUE('Type Of Working Hour'[Type Of Working Hour]) = "Subcontractor", SUM('Working Hour'[Number Of Subcontractor Hours]),         SELECTEDVALUE('Type Of Working Hour'[Type Of Working Hour]) = "Joint Venture", SUM('Working Hour'[Number Of Joint Venture Hours]),         // Employee + Subcontractor         COUNTROWS (SelectedValues) = 2 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Employee") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Subcontractor"),          SUM('Working Hour'[Number Of Employee Hours]) +  SUM('Working Hour'[Number Of Subcontractor Hours]),         // Employee + Joint Venture         COUNTROWS (SelectedValues) = 2 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Employee") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Joint Venture"),          SUM('Working Hour'[Number Of Employee Hours]) + SUM('Working Hour'[Number Of Joint Venture Hours]),         // Employee + Temporary         COUNTROWS (SelectedValues) = 2 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Employee") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Temporary"),          SUM('Working Hour'[Number Of Employee Hours]) + SUM('Working Hour'[Number Of Temporary Hours]),         // Temporary + Subcontractor         COUNTROWS (SelectedValues) = 2 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Temporary") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Subcontractor"),          SUM('Working Hour'[Number Of Temporary Hours]) + SUM('Working Hour'[Number Of Subcontractor Hours]),         // Temporary + Joint Venture         COUNTROWS (SelectedValues) = 2 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Temporary") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Joint Venture"),          SUM('Working Hour'[Number Of Temporary Hours]) + SUM('Working Hour'[Number Of Joint Venture Hours]),         // Subcontractor + Joint Venture         COUNTROWS (SelectedValues) = 2 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Subcontractor") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Joint Venture"),          SUM('Working Hour'[Number Of Subcontractor Hours]) + SUM('Working Hour'[Number Of Joint Venture Hours]),         // Employee + Subcontractor + Joint Venture         COUNTROWS (SelectedValues) = 3 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Employee") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Subcontractor") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Joint Venture"),          SUM('Working Hour'[Number Of Employee Hours]) + SUM('Working Hour'[Number Of Subcontractor Hours]) + SUM('Working Hour'[Number Of Joint Venture Hours]),         // Employee + Subcontractor + Temporary         COUNTROWS (SelectedValues) = 3 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Employee") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Subcontractor") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Temporary"),          SUM('Working Hour'[Number Of Employee Hours]) + SUM('Working Hour'[Number Of Subcontractor Hours]) + SUM('Working Hour'[Number Of Temporary Hours]),         // Employee + Joint Venture + Temporary         COUNTROWS (SelectedValues) = 3 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Employee") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Joint Venture") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Temporary"),          SUM('Working Hour'[Number Of Employee Hours]) + SUM('Working Hour'[Number Of Joint Venture Hours]) + SUM('Working Hour'[Number Of Temporary Hours]),         // All Selected         COUNTROWS (SelectedValues) = 4 &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Employee") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Subcontractor") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Joint Venture") &&         CONTAINSSTRING (CONCATENATEX (SelectedValues, 'Type Of Working Hour'[Type Of Working Hour], ","), "Temporary"),          [Total Working Hours],          [Total Working Hours]     )
```
## Total Working Hours - Project

Model table: `Measure`

```dax
 SUMX(FILTER('Working Hour','Working Hour'[DimProjectId]<>-1) ,   'Working Hour'[Number Of Employee Hours]                                                    		        + 'Working Hour'[Number Of Joint Venture Hours]                                                    			   + 'Working Hour'[Number Of Subcontractor Hours]                                                    			   + 'Working Hour'[Number Of Temporary Hours])
```
## Total Working Hours DEME

Model table: `Measure`

```dax
 SUMX('Working Hour',   'Working Hour'[Number Of Employee Hours]                                                			  + 'Working Hour'[Number Of Temporary Hours])
```
## Total Working Hours DEME - Entity

Model table: `Measure`

```dax
 SUMX(FILTER('Working Hour', 'Working Hour'[DimEntityId]<>-1),   'Working Hour'[Number Of Employee Hours]                                                                 			   + 'Working Hour'[Number Of Temporary Hours]) 
```
## Total Working Hours DEME - Project

Model table: `Measure`

```dax
 SUMX(FILTER('Working Hour','Working Hour'[DimProjectId]<>-1),   'Working Hour'[Number Of Employee Hours]                                                                 			     + 'Working Hour'[Number Of Temporary Hours])
```