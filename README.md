
My Solution to [India ML Hiring Hackathon 2019](https://datahack.analyticsvidhya.com/contest/india-ml-hiring-hackathon-2019/) on [Analytics Vidhya](https://www.analyticsvidhya.com/) using Python3.
## ***[View Solution (.ipynb)](https://nbviewer.jupyter.org/github/akki3d76/India-ML-Hiring-Hackathon-2019/blob/master/CODE_ML_2019.ipynb)***

# Problem Statement

##  Loan Delinquency Prediction
Loan default prediction is one of the most critical and crucial problem faced by financial institutions and organizations as it has a noteworthy effect on the profitability of these institutions. In recent years, there is a tremendous increase in the volume of non – performing loans which results in a jeopardizing effect on the growth of these institutions.

Therefore, to maintain a healthy portfolio, the banks put stringent monitoring and evaluation measures in place to ensure timely repayment of loans by borrowers. Despite these measures, a major proportion of loans become delinquent. Delinquency occurs when a borrower misses a payment against his/her loan.

Given the information like mortgage details, borrowers related details and payment details, our objective is to identify the delinquency status of loans for the next month given the delinquency status for the previous 12 months (in number of months) 
<h2 id="data-description">Data Description</h2>
<h3 id="data-dictionary">Data Dictionary</h3>
<table dir="ltr" border="1" cellspacing="0" cellpadding="0"><colgroup><col width="100" /><col width="368" /></colgroup>
<tbody>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Variable&quot;}"><strong>Variable</strong></td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Description&quot;}"><strong>Description</strong></td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;loan_id&quot;}">loan_id</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Unique loan ID&quot;}">Unique loan ID</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;source&quot;}">source</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Loan origination channel&quot;}">Loan origination channel</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;financial_institution&quot;}">financial_institution</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Name of the bank&quot;}">Name of the bank</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;interest_rate&quot;}">interest_rate</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Loan interest rate&quot;}">Loan interest rate</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;unpaid_principal_bal&quot;}">unpaid_principal_bal</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Loan unpaid principal balance&quot;}">Loan unpaid principal balance</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;loan_term&quot;}">loan_term</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Loan term (in days)&quot;}">Loan term (in days)</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;origination_date&quot;}">origination_date</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Loan origination date&quot;}">Loan origination date (YYYY-MM-DD)</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;first_payment_date&quot;}">first_payment_date</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;First instalment payment date&quot;}">First instalment payment date</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;loan_to_value&quot;}">loan_to_value</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Loan to value ratio&quot;}">Loan to value ratio</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;number_of_borrowers&quot;}">number_of_borrowers</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Number of borrowers&quot;}">Number of borrowers</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;debt_to_income_ratio&quot;}">debt_to_income_ratio</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Debt-to-income ratio&quot;}">Debt-to-income ratio</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;borrower_credit_score&quot;}">borrower_credit_score</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Borrower credit score&quot;}">Borrower credit score</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;loan_purpose&quot;}">loan_purpose</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Loan purpose&quot;}">Loan purpose</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;insurance_percent&quot;}">insurance_percent</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Mortgage insurance percent&quot;}">Loan Amount percent covered by insurance</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;co-borrower_credit_score&quot;}">co-borrower_credit_score</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Co-borrower credit score&quot;}">Co-borrower credit score</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;insurance_type&quot;}">insurance_type</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Mortgage insurance type&quot;}">0 - Premium paid by borrower, 1 - Premium paid by Lender</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;m1 to m12&quot;}">m1 to m12</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;Month-wise loan performance (deliquency in months)&quot;}">Month-wise loan performance (deliquency in months)</td>
</tr>
<tr>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;m13&quot;}">m13</td>
<td data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;target, loan deliquency status (0 = non deliquent, 1 = deliquent)&quot;}">target, loan deliquency status (0 = non deliquent, 1 = deliquent)</td>
</tr>
</tbody>
</table>


## Evaluation Metric 
**F1-score**  between the predicted and observed class** 

## LeaderBoard Results
![enter image description here](https://lh3.googleusercontent.com/O19r9kC5vp9I642AE8orLDXDdX0seU4t4flzOcuPL0TLnkTeB_0uK_Py1vDpGzMrX1Xjy4duQjTq)

Public Leaderboard
![enter image description here](https://lh3.googleusercontent.com/UBvwd1PgAXY671A41nLP_thOcDUMG7WFe9Afww_eXWZDGyrSBXgmf4MsaKBIKumTLoZoTfDrkBPw)

Private Leaderboard
![enter image description here](https://lh3.googleusercontent.com/TyaCkeLVyvJMKSWohrs73hIIEpo_Zb9VrQ4bXiFX4UzsTSYfT3mu93TDNmBvH0tKiuffBDayxlKS)
