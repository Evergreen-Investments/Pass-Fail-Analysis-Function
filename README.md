# Pass-Fail Analysis Function

The Pass-Fail Analysis Function is a function created within the Zoho CRM to look at the Property Database Module, compare Seller's Desired Net field and Conservative Net to Seller Field, and change the Status to "Pass/Fail Analysis" based on whether Desired Net is less than or equal to Conservative Net Seller.

## Solution Creation
1. Edit the arguments and made the “key” name and Property_ID. This would allow us in the first line to access all the information of each account by using "getRecordBy "
```bash
Recs = zoho.crm.getRecordById("PropertyDatabase", Property_ID);
```
2.Create a variable “SellerDN” where we accessed the sellers desired net by using “get” and finding the corresponding APIs.
```bash
SellerDN = Recs.get("Asking_Price");
```
3.Repeat with Conservative Net to Seller data
```bash
ConNTS = Recs.get("MaxBidWholesalerRound");
```
4. Compare them using a if else conditional.
```bash
if ( SellerDN <= ConNTS)
```
5.If the sellers desired net was less than the conservative net to seller value then it will update the status of the account as “Pass Analysis”, by using “Map()”, which allows us to take a variable with the new value, and put it into the “status” field in the account.
```bash
	Status_Update = Map();
	Status_Pass = "Pass Analysis";
	Status_Update.put("Status", Status_Pass);
```
6.For the Else aspect this is where the "Fail Analysis" is updated by using the same “put” function.
```bash
  Status_Update = Map();
	Status_Fail = "Fail Analysis";
	Status_Update.put("Status", Status_Fail);
```
7.Finally, make a variable outside of the condition to actually push the Update into the account, using "zoho.crm.UpdateRecord" along with already used the already made variables as the parameters.
```bash
Update = zoho.crm.UpdateRecord("PropertyDatabase", Property_ID, Status_Update);
```

## Diagram
<img width="863" alt="Screen Shot 2023-02-08 at 2 02 15 PM" src="https://user-images.githubusercontent.com/124835662/217654741-f3d49892-3801-4a6f-b905-f5c1ba709e84.png">
