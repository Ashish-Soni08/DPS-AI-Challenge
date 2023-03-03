# Digital Product School AI Engineering Challenge

## Objective of the Challenge

Create an AI model for [Monatszahlen Verkehrsunfälle (Monthly Figures for traffic accidents)](https://opendata.muenchen.de/dataset/monatszahlen-verkehrsunfaelle/resource/40094bd6-f82d-4979-949b-26c8dc00b9a7) Dataset that includes the following accident types -> traffic accidents, flight accidents, alcohol accidents per month that happened in Munich, Germany. Then Deploy the model to a cloud service.

### Instructions

#### Mission 1: Create an AI Model

1. The first 5 columns are Important:
   - Category
   - Accident-type (insgesamt means total for all subcategories)
   - Year
   - Month
   - Value

2. Drop the records which come after 2020 for developing the prediction model.

3. Create a visualization to plot the number of accidents per category

4. Create an application that forecasts the values for (Example):
   - Category: 'Alkoholunfälle'
   - Type: 'insgesamt
   - Year: '2021'
   - Month: '01'  

## Data Dictionary

| Column_Name(Deutsch) | Column_Name(English) | Column_Type |
| --- | --- | --- |
| MONATSZAHL | Category | text |
| AUSPRAGUNG | Accident-type | text |
| JAHR | Year | numeric |
| MONAT | Month | text |
| WERT | Value | numeric |
| VORJAHRESWERT | Previous-year | numeric |
| VERAND_VORMONAT_PROZENT | Change-from-previous-month-percentage | text |
| VERAND_VORJAHRESMONAT_PROZENT | Change-from-previous-year-month-percentage | text |
| ZWOLF_MONATE_MITTELWERT | 12-month-average | text |

**Data last updated:** 28. November 2022

**Metadata last updated:** 20. Februar 2017

**Size:** 150,9 KiB

```bash

# Download the data as a csv file
wget https://opendata.muenchen.de/dataset/5e73a82b-7cfb-40cc-9b30-45fe5a3fa24e/resource/40094bd6-f82d-4979-949b-26c8dc00b9a7/download/monatszahlen2209_verkehrsunfaelle.csv

```

Create and Activate the virtual environment for the project

```bash
# create
python -m venv dps-ai

# activate 
source /workspaces/DPS-AI-Challenge/dps-ai/bin/activate
```

### Mission 2: Publish your source code and Deploy

Publish your source code in a github repository. The next step is to deploy the model. Create an endpoint that returns your predictions. Make sure that your endpoint accepts a POST request with a JSON body like this:

```markdown
{
"year":2020,
"month":10
}
```

And it should return your applications prediction in the following format:

```markdown
{
"prediction":value
}
```

### Mission 3: Send DPS the URL of the work

Make a POST request to the following URL.

`https://dps-challenge.netlify.app/.netlify/functions/api/challenge`

#### Body

The body of the request should be JSON format, like below:

```markdown
{
"github":"https://github.com/ACCOUNT/REPO",
"email":"EMAIL",
"url":"DEPLOYED_ENDPOINT", 
"notes":"NOTES" // Not mandatory
}
```

Fill in the email address for EMAIL, the path to your github repo at ACCOUNT/REPO and the link of your deployed model at DEPLOYED_ENDPOINT.

At NOTES, write some notes to DPS. These notes can be anything you would like DPS to know, especially for technical decisions. They are not mandatory, so you can also skip this this parameter.

#### Content type

The Content-Type of the request must be application/json

#### Sample Request

```markdown

POST https://dps-challenge.netlify.app/.netlify/functions/api/challenge
Content-Type: application/json 

{
"github":"https://github.com/DigitalProductschool/website",
"email":"name@example.com",
"url":"https://digitalproductschool.io/", 
"notes":"I deployed using ..." // Not mandatory
}
```

#### Sample Response

If your POST request succeeds, the server returns HTTP status code 200.

```markdown

Status 200 OK 
{"message":"Congratulations! Achieved Mission 3"}

```
