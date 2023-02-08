# Pass-Fail Analysis Function

The Pass-Fail Analysis Function is a function created within the Zoho CRM to look at the Property Database Module, compare Seller's Desired Net field and Conservative Net to Seller Field, and change the Status to "Pass/Fail Analysis" based on whether Desired Net is less than or equal to Conservative Net Seller.

## Solution Creation

1. Edit the arguments and made the “key” name and Property_ID. This would allow us in the first line to access all the information of each account by using getRecordBy 

2.Create a variable “SellerDN” where we accessed the sellers desired net by using “get”.
```bash
Recs = zoho.crm.getRecordById("PropertyDatabase", Property_ID);
```

3.Repeat with Conservative Net to Seller data

4. Compare them using a if else conditional. We made it so that if the sellers desired net was less than the conservative net to seller value then we will update the status of the account as “Pass Analysis”. We did this by using “Map()’” which allows us to take a variable with the new value and put it into the “status” field in the account. For the Else aspect this is where we did the Fail Analysis update by using the same “put” function. Finally we made a variable outside of the condition to actually push the Update into the account. We used zoho.crm.UpdateRecord and used the already made variables as our parameters.

## Diagram
<img width="863" alt="Screen Shot 2023-02-08 at 2 02 15 PM" src="https://user-images.githubusercontent.com/124835662/217654741-f3d49892-3801-4a6f-b905-f5c1ba709e84.png">
