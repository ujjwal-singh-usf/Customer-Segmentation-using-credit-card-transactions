### Introduction: This program will help in targeting customers with high volume transactions on cabs services in the previous 3-4 months by consolidating their number of transactions per month.

Approach:
	The Program uses the total number of cabs with matching keywords ‘uber’ and ‘lyft’ in past 3 months based on related merchant category to shortlist the customers for promotions.

About the Program:

Conditions:
•	Data Should be present till the last month
•	Input data of the months considered should be complete i.e till end of every month

Required Input Data:
1.	Input card transaction data file (txt or csv format)
Brief Description of the Program Logic:
•	The Program reads the input card transaction data in chunks to read large amount of data.
•	The ‘rental tags’ are used to identify the merchant categories related to cab transactions and the data is sliced only for those categories.
•	The cab transactions are marked in a new column ‘auto_txn_tag’.
•	For each customer the program compares the given minimum limit of transactions for cabs against each of their past 3 months transactions count. If a customer has made transactions in previous 3 months which crosses the min limit, the customer is shortlisted as uber/lyft. 
•	For the shortlisted customers the program analyzes all the cabs transactions in relevant group and generates a pivot table name with no of transactions in each month.
Notes/Other Instructions:
•	Incase if the name of Merchant categories related to cab transactions change in future, the rental tag needs to be adjusted accordingly to ensure successful code run.

Example Output:
The Program creates 2 output data frames
1.	Uber_Pivot – Pivot table with customers spent on Uber and their number of transactions for each month.
2.	Lyft_Pivot - Pivot table with customers spent on Lyft and their number of transactions for each month.
