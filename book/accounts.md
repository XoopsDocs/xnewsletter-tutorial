## 2.1 Accounts

On this tab you can see an overview of your existing accounts.
You can use one or more email accounts for sending the newsletters.
![](../assets/accounts1_en.PNG)

You have the possibility to create an account for sending
* with php mail() function
* with php sendmail() function
* via a pop3 email account
* via a smtp email account
* via a google email account

Example for an account using php mail() function
![](../assets/accounts3_en.PNG)

Example for an account using a smtp mail account
![](../assets/accounts4_en.PNG)


There is a feature for testing pop3 and imap accounts.
![](../assets/accounts2_en.PNG)

After starting the test you will see, whether the account and your chosen setting are well.

>![](../assets/info/important.png) **Pay attention:** 
1. **xnewsletter is not creating an email account** - the account must already exist
2. functions like testing account, sending emails, start Bounced email handler,... work not with local server (you get white page without any error)