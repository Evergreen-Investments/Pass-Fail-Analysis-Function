# Pass-Fail Analysis Function

The Pass-Fail Analysis Function is a function created within the Zoho CRM to look at the Property Database Module, compare Seller's Desired Net field and Conservative Net to Seller Field, and change the Status to "Pass/Fail Analysis" based on whether Desired Net is less than or equal to Conservative Net Seller.

## Solution Creation

First, we edited the arguments and made the “key” name and Property_ID. This would allow us in the first line to access all the information of each account by using getRecordBy Then we created a variable “SellerDN” where we accessed the sellers desired net by using “get”. We then did the same thing to get the conservative net to seller data. Once we had these values we were able to compare them using a if else conditional. We made it so that if the sellers desired net was less than the conservative net to seller value then we will update the status of the account as “Pass Analysis”. We did this by using “Map()’” which allows us to take a variable with the new value and put it into the “status” field in the account. For the Else aspect this is where we did the Fail Analysis update by using the same “put” function. Finally we made a variable outside of the condition to actually push the Update into the account. We used zoho.crm.UpdateRecord and used the already made variables as our parameters.

## Diagram
