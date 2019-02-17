#### Objective: Clean card transactions data to identify and segment customers through spending patterns and use them for promotions, customers retention and cross-sell programs.  

Introduction: This program will help in identifying customers/ couples who married recently or getting married in near future.

Approach:
	The program group customers into three categories based on keywords and merchant type 1. large transactions (hotels, jewelry, catering, florists) 2. bridal stores and 3. photography only if the posted amount cross a minimum threshold for each keyword. Creates a pivot table and assigns probability against all shortlisted customers based on the number of categories satisfied. 
About the Program:

Conditions:
•	Data Should be present till last month. From last month till past 9 to 12 months of data should be ideal input.
•	Run the program in First or second week of the month by using data till last month.

Required Input Data:
1.	Input card transaction data file (txt or csv format).
2.	Wedding Keywords file (Wedding_Keywords.xls file)

Brief Description of the Program Logic:
•	The Program reads the input card transaction data in chunks to read large amount of data.
•	Grouped the data into three categories based on keywords, merchant type and post amount and assign a probability score for each.
•	The customers are flagged for Large Transactions by parsing a list of keywords for hotels, jewelry, florists and catering against the clean merchant category.
•	Group 1: Large is created by grouping these transactions and checking for a min threshold and convert into a table with probability as ‘None’, category as ‘Large’ and ‘Clean_Name’
•	The customers are flagged for Bridal Stores by parsing a list of search terms against the cardacceptername and eliminating other non-relevant categories defined in ‘other_cat’.
•	Group 2: Bridal Stores is created by grouping these transactions and checking for a min threshold and convert into a table with probability as ‘Low, category as ‘Bridal’.
•	The data is sliced for ‘Commercial Photography’ in the merchant category.
•	Group 3: Photography is created by grouping these transactions and checking for a min threshold and convert into a table with probability as ‘Low, category as ‘Photography’.
•	Groups 1, 2 and 3 are concatenated together and a dictionary is created for scoring with ‘ArtificialAccountKey’ as the key and ‘clean_name’, ‘probability’ and ‘category’ as values.
•	For each customer in the final group, below logic has been used for final scoring.
•	If customer is present in Group 2 and 3 -> change the Probability as ‘High’
•	If customer is present in Group 1 and either of (Group 2 or 3)-> change the Probability as ‘Medium’
•	If customer is present in all the three Groups 1, 2 and 3 -> change the Probability as ‘Very_High’
•	If there are no matches -> the probability remains unchanged.
•	The scored dictionary is converted into a table with customer key, card_acceptor_name, category, probability and all the unscored customers are eliminated.
