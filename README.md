# Code Sample

This notebook presents a shortened example of my past work on election data for political campaigns. It focuses on cleaning and analyzing voter data from the North Carolina Secretary of State's office to build a predictive model that estimates the probability of each voter turning out in the 2024 general election. These models are often used to help campaigns understand their electorate, optimize outreach strategies, and tailor messaging. Below is a breakdown of my approach.

## Data Cleaning & Pre-Processing

This example turnout model is built for Alamance County, NC using publically available [vote history](https://www.ncsbe.gov/results-data/voter-history-data) and [voter file](https://www.ncsbe.gov/results-data/voter-registration-data). Before modeling, I performed several pre-processing steps:
* For the vote history data, I simplified and restructured the election results and handled null votes (people who did not vote in the election) by imputing with 0.
* For the voter file data, I did some basic collapsing of voter file status and one hot encoded birth state, driver’s license, race, ethnicity, and gender to use as predictors in the model.

I then constructed two modeling frames:
* "Historical" modeling frame - Uses the 2020 general election as its reference point and is used to train the model.
* "Current" modeling frame - Uses the 2024 general election as its reference point and is used to generate predictions.
Additionally, I derived features like age and years since registration for both frames.

## Modeling

To predict voter turnout, I trained a LASSO logistic regression model using the
2020 "historical" modeling frame. Feature selection was based on cross-validated ROC-AUC performance, with key predictors including SOS voter status, previous vote history, and gender. I then applied the trained model to the "current" modeling frame, generating turnout probability scores for each voter.

## Analysis

The final section of this notebook demonstrates how this model can be used for analysis, including:
* Turnout Propensity Distribution - Examining how well the model separates likely and unlikely voters.
* Turnout by Age Group - Understanding how voting likelihood varies across different demographics.

This analysis could be expanded in a number of ways:
* Examining turnout likelihood across race, gender, or voting history.
* Analyzing geographic patterns (ex: turnout by neighborhood)
* Incorporating additional data (education, income, voter registration trends)
* Repeating modeling across additional elections to assess the impact of policy changes or voter enthusiasm.

Thank you for viewing this code sample, and I welcome any questions/comments.
