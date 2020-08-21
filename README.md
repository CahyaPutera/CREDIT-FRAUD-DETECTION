## Tugas IYKRA Data MBA.
# TRANSACTION DATA (CREDIT FRAUD) - EDA
“Data Transactions” (transactions.csv) - Fix dataset digunakan untuk usecase fraud dan clustering.

# FEATURE DESCRIPTION :

- accountNumber             = The account number of The customer
- customerId    =  The ID of The customer
- creditLimit               =  The amount of money that can be charged to The debit card
- availableMoney        = The amount of money in The debit card before adjusting for pending charges      
- transactionDateTime       = The transaction timestamp when it happened
- transactionAmount        = The amount of transaction 
- merchantName          = The merchant name of The particular transaction
- acqCountry             = The country where The merchant is located
- merchantCountryCode    = The country code for The specific merchant
- posEntryMode        = a code that tells The processor how The transaction was captured
- posConditionCode   = a code identifying transaction conditions at The point-of-sale or point-of-service
- merchantCategoryCode    = The merchant category/types
- currentExpDate       =  The expiry date of The credit card
- accountOpenDate      = The date when The customer open The credit card
- dateOfLastAddressChange    = The last date when The customer change The credit card address
- cardCVV = The actual card verification value
- enteredCVV       = The entered card verification value
- cardLast4Digits     = The last 4 digits of The debit card
- transactionType        = The types of transactions
- isFraud      = The status of The fraud transaction
- echoBuffer    = number of delayed response transactions
- currentBalance =  The current balance of The debit card
- merchantCity = The location for The specific merchant (City)
- merchantState   = The location for The specific merchant (State)
- merchantZip = The location for The specific merchant (Zip Code)           
- cardPresent =     The physical presence of The debit card in The transaction
- posOnPremises = The location of The point of sales          
- recurringAuthInd  = wheTher The auThentication recurred or not
- expirationDateKeyInMatch = The match between The expiration date in The system and what was inputted
