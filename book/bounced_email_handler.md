# 2.10 Bounced email handler (BMH)

On this tab you can see an overview of the results of the last run BMH.

![](../assets/bmh1_en.PNG)

If you run BMH, the module will check your email account for bounced mails.
Mails, which are detected as bounced emails by BMH, can be deleted or moved in a special folder, you have to define.
Possible actions for Bounced emails:
-- no action (only store)
-- quit temporary the subscriptions of this email-address
-- delete the subscriptions of this email-address


#### Types of Bounced emails
**bounce type hard:** This means that there is a permanent error when sending a mail, e.g. unknown recipient, unknown domain, and so on.
This mails will be deleted after detection, so it is recommended using the move hard option (the email will be only moved in this folder, you can check this mail later, if you want).

**bounce type soft:**
This means that there is a temporary problem with sending a mail, e.g. mailbox full, server not available, and so on.
This mails will not be deleted after detection, but it is recommended using the move soft option in order to keep your basic in box clean.

Pay attention: functions like testing account, sending emails, start Bounced email handler,... work not with local server (you get white page).