# NPPES-CONTACT-VERIFICATION-WEB-APP

## Overview
This project is a challenge on [Topcoder](https://www.topcoder.com/challenges/c587c6b7-f378-4dc7-bb4b-29fb12174025).

The challenge requires a Node app, with a basic UI that can take an Excel spreadsheet as input, and then go through and validate the:

- Address 
- city
- State
- Country
- Phone number
- Fax Number

to a certain amount of certainty.

This challenge targets NPPES and its API for validation of the fields above.

The output is the same excel sheet with additional columns with the suggested data that had been found on NPPES and how sure the app is of the suggested data

## Details of the validation process

- The app uses first name and last name for searching. Names with special characters can't found on NPPES API and names with space or '-' must be removed before searching

- The NPPES API return only results with matched first name and last name so we don't need to validate the names or include them in the surety percent

- The app validates 6 pieces of informations which are address, city, state, country, phone, fax. Each one has it's own surety percent

- The surety percent of the suggestions is the (sum of all surety percents) / 6

- People with blank suggestions and surety percent not found on NPPES API

- People with '0 %' surety percent found but the only match is the first name and last name (most of them are the ones that their names include space or '-')

- For surety percent of state, country, phone, fax the percent is either 0 or 1

- For surety percent of address, city the percent is the (number of matched words)/ (the number of words in the largest string). That is because both of them can be written in many different ways.

- For city, comparing "SAINT JOSEPH" with "St. Joseph" will result 1/2 surety percent

- For address, comparing "501 DR MICHAEL DEBAKEY DR" with "501 Dr. Michael DeBakey Drive" will result 3/5 surety percent

- The app calculates the surety percent for every person in the NPPES API respnose and save the one with the biggest surety percent and suggest his data, so if someone has '0 %' surety percent that means he has only one result for him and that result match only his first name and last name



## Built with
- Node.js
- Express
- Flutter


## Demo


https://user-images.githubusercontent.com/63409218/195948227-5bb1a975-e633-466e-becb-1784b4de1652.mp4


### Sample input
[input.xlsx](https://github.com/mohamedhesham1619/NPPES-CONTACT-VERIFICATION-WEB-APP/files/9790213/input.xlsx)

### Sample output with the additional columns

[output.xlsx](https://github.com/mohamedhesham1619/NPPES-CONTACT-VERIFICATION-WEB-APP/files/9790217/output.xlsx)

