# Simba-and-Co
Simba and Co project for Erdos Institute 2021 Bootcamp: Cover My Meds
Apostolos Zournas, Diego Prado, Bhargava Nemmaru
## Problem Statement
CoverMyMeds (CMM) is a healthcare information technology company that strives to ‘help patients get the medication they need’, by automating the process of prior authorizations (PA). According to a report by Health Affairs, prior authorizations cost between $23 to $31 billion USD, including the time spent by healthcare providers to fill out these forms and leading to reduced patient outcomes. CMM addresses the need to simplify this process by providing electronic PA (ePA) forms in lieu of a complicated application process which would otherwise require coordination between care providers, insurance companies, pharmacies, and the patients. The success of this service has led to generation of rich data sets which can be harnessed to better serve patients and their respective healthcare providers, while streamlining CMM’s business processes. This study focused on addressing two questions, using various data science tools:
1. Predicting whether or not a claim will be approved, based on drug type and payer information
2. Forecasting short-term and long-term ePA volume based on historical data 

**Data science based solutions:** We used support vector machines (SVMs) to address the first question and achieved an accuracy of ~93%. We tested the robustness of the model by employing a precision recall curve and also ran analysis to test the computational time needed for training the model.  We used recurring neural networks (RNNs) and time series analysis based on Holt-winters’ seasonality method to forecast PA volume from the existing data

## 1. Predicting approval of claims based on drug type and payer (Bhargava Nemmaru, Apostolos Zournas)
### 1. Predicting approval of claims
### 2. Predicting approval of a PA
We used a feed-forward neural net to predict whether a rejected claim would be approved due to a PA. We did this with 74% accuracy. 

## 2. Forecasting short- and long-term PA volume based on historical data (Diego Prado, Apostolos Zournas)
### Exponential Smoothing Model using Holt-Winters' Additive Seasonality Method
Using the provided data sets of claim results and dates of claims, we created a time series dataframe to forecast short-term and long-term PA volume. We observed a layer of seasonality per week as well as per year; we also observed a trend of increased volume over time. As we are limited to only three years of data, we restricted our analysis to seasonality per week. Using the Holt-Winters’ seasonality method for triple exponential smoothing, we created an additive model of time series fit and forecasting. This method is ideal for modeling time-series data with differing trends over time and a seasonality. We observed that this model could fit the overall data rather well and, with the exception of holidays, could forecast PA volume up to ~180 days. However, due to weekly, monthly, and yearly variations, this model appears to be more efficient at forecasting long-term PA volume rather than shorter changes
<br>
<br>
**Summary outcome:** Model allows prediction of long-term PA and claim volume with good accuracy and short term with less accuracy but ignores variation from holidays
### Recurring Neural Net
We implemented an RNN to predict the total claims, claims approved and PAs approved. The RNN takes as an input the variable we want to predict for 50 days and predicts the same variable for the next 7 days. It predicts accurately for these parameters, but cannot make long-term predictions, and so cannot predict the long-term, yearly seasonality as accurately.

## Stakeholder value propositions: 
There are four key stakeholders in this business model: (i) CoverMyMeds (ii) healthcare providers (iii) pharmacies (iv) patients. The above-mentioned problem statements were chosen based on their potential to deliver value to stakeholders. For instance, our first solution based on SVMs allows healthcare providers to assess the situation and assign an ePA seamlessly, which saves hassles both for physicians and eventually the patients. CMM’s revenue model is based on the sale of ePAs and forecasting the ePA volume could be a great indicator of short-term and long-term revenue. In addition, this can also allow for hypothesis testing of new business and marketing strategies. 
