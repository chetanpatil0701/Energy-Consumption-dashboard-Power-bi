# Energy-Consumption-dashboard-Power-bi
A dynamic Dashboard Showing Energy Consumption

#Detailed Discription
Data Source=Kaggle.com

#Data structure-
1.Format-Excel Workbook
2.No.of Sheets-3

1st Sheet-Energy consumption-:Given the amount of Energy(water,electricity and Gas)consumed by the Buildings.
5 colums ie.Date,Building,water consumption,Electricity Consumption and Gas Consumption.and no. of rows are 529

2nd sheet-Rates-:Given the rates for each unit of energy according to year.
3 colums ie. Year,Energy type and price per unit and no. of rows are 16.

3rd sheet-Building Master-:Given the building number ,state and city.
3 columns and 12 rows.

#Data Import
1.open powerbi desktop and go to blank report
2.click on import data from excel then double tap on data file and select all 3 worksheets and click on transform data to open power Query editor for data cleaning

#Data Cleaning
1.check all datatypes and column headings.
2.Remove null values by clicking on Remove empty in energy consumption query.
3.click on use first row as header in Building Master sheet.

#Data Manipulation-for proper analysis we have to append 3 energy types.
1.in energy consumption sheet click on transform and select add suffix from format tab then add suffixes W,E and G for water, electricity and Gas respectively.
2. then duplicate same sheet 2 more times in first duplicate delete colums electricity and Gas consumption.and rename that column as 'energy consumption'.
3.in 2nd duplicate remove water and Gas consumption and rename that column as 'energy consumption'.
4. in original remove water and electricity consumption columns and rename that column as 'energy consumption'.
5. after that go on first duplicate and in home tab select append queries then click on 3 or more tables and add that 2 remaining duplicates below the first and click on ok.
6. select energy consumption column and select extract tab from add column section and click on last character and extract 1 character ie suffixes .
7.then rename the column as energy type and click on replace values and replace W as Water ,E as Electricity and G as gas.then click on close and apply.

after close and apply delete the unwanted queries or tables.

#Dax- for creating measures useful for data analysis.

1.electricity cost = CALCULATE([Total cost],'Energy Consumptions'[Energy type]="electricity")
2.Electricity cost left = [Total cost]-[electricity cost]
3.electricity left = [total consumption]-[total Electricity consumption]
4.Electricity% = CALCULATE([total Electricity consumption]/SUM('Energy Consumptions'[units]))
5.Gas cost = CALCULATE([Total cost],'Energy Consumptions'[Energy type]="Gas")
6.Gas cost left = [Total cost]-[Gas cost]
7.Gas left = [total consumption]-[total Gas consumption]
8.Gas% = CALCULATE([total Gas consumption]/SUM('Energy Consumptions'[units]))
9.total consumption = sum('Energy Consumptions'[units])
10.Total cost = SUMX('Energy Consumptions','Energy Consumptions'[units]*RELATED(Rates[Price Per Unit]))
11.total Electricity consumption = CALCULATE(SUM('Energy Consumptions'[units]),'Energy Consumptions'[Energy type]="Electricity")
12.total Gas consumption = CALCULATE(SUM('Energy Consumptions'[units]),'Energy Consumptions'[Energy type]="Gas")
13.total water consumption = CALCULATE(SUM('Energy Consumptions'[units]),'Energy Consumptions'[Energy type]="water")
14.Water cost = CALCULATE([Total cost],'Energy Consumptions'[Energy type]="water")
15.water cost left = [Total cost]-[Water cost]
16.water left = [total consumption]-[total water consumption]
17.Water% = CALCULATE([total water consumption]/SUM('Energy Consumptions'[units]))

#visualization


