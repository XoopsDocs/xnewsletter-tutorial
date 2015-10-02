# 4.0 Operating Instructions

#### Basic information

The module is based on PHPMailer and PHPMailer-BMH 

#### (Un) subscriptions to newsletters
You can define for each group, whether for (un) subscription or change a confirmation email with activation key is necessary or not (use double-option).

#### Create a newsletter
The newsletter can be created with each text editor which is installed in current xoops core (e.g. TinyMCE). 
For each newsletter you can use different templates (see also 'Newsletter templates').
You can define one or more newsletter categories for your newsletter.
You can add 5 files maximum as attachment to each newsletter.

Optionally you can also copy an older newsletter and edit or send it as a new one.

The type of text editor, allows mime-types and size of mail attachments can be set in module preferences.


#### Newsletter templates
The newsletters are template based.
The templates are stored as files in language/{yourlanguage}/templates or stored in database.
To create a new template you can:
- make a new template html-file in in language/{yourlanguage}/templates folder and to put in the smarty-vars;
- from admin side create a new template item and to put in the smarty-vars.

This module uses the XOOPS [Smarty template engine](http://www.smarty.net/) to render the email letter.

Available smarty-vars are:
- <{$salutation}> or <{$sex}>: the subscriber Salutation field
- <{$firstname}>: the subscriber First name field
- <{$lastname}>: the subscriber Last name field
- <{$email}> or <{$subscr_email}>: the subscriber Email field
- <{$title}>: the newsletter Title field
- <{$content}>: the newsletter Content field
- <{$date}>: the sending date as timestamp integer<br> 
  (e.g.: <{$date|date_format:"%Y/%m/%d"}> will output the date formatted as 2001/01/04)
- <{$unsubscribe_url}>: the unsubscribe url
- <{$xoops_url}>: the site main url (e.g. http://localhost/)
- <{$xoops_langcode}>: the site langcode (e.g. en)
- <{$xoops_charset}>: the site cherset (e.g. UTF-8)


#### Sending newsletter
You can show a preview of a newsletter before sending.
You can send the newsletter for testing to a defined email-address.
The newsletters will be sent subscriber by subscriber.
For each sending action a protocol will be created.
If one or more send failed, you can see it in the protocol.
You can restart sending procedure. You can send it again to all subscribers or send it only to the subscribers, where sending procedure failed).

You can send all emails immediately or limit emails send in one package.
The number of emails and the minutes until next sending can be defined in module preferences (e.g. 200 emails all 60 minutes).
The first package will be sent immediately. To start the next sending procedure you need an external cronjob, which is calling "../modules/xnewsletter/cron.php". Xoops cannot do this with current version (2.5.5).

Pay attention: functions like testing account, sending emails, start Bounced email handler,... work not with local server (you get white page).

#### Task list
If you limit emails send in one package, you can see all newsletters waiting for next cronjob and the time, when cronjob can send the newsletter.
If you do not use this option, the tab "Task list" is hidden.

#### Handle mailing lists
If you have an existing mailing list, you can synchronize the (un) subscriptions of one newsletter category with one mailing list.
I use majordomo beside this newsletter module because then I can also send an email from my email-client to the newsletter recipients.
One of the disadvantages of mailing lists is, that, if one person is registered in two or more mailing lists and you send a one newsletter to all mailing lists, this person gets the same newsletter more than one time. With xNewsletter he gets only one newsletter.


Normally the tab "Mailing list" is hidden, if this option is disabled.

>![](../assets/info/important.png) **IMPORTANT:** xNewsletter cannot create mailing lists. 

#### Bounced email handler (BMH)
If you send newsletters, there will always be some emails not delivered to recipient (Bounced email), because email is no more valid, mailbox is full, and so on.
To handle this event and to react on this, you can use BMH.
You can activate BMH for each account.
Mails, which are detected as Bounced emails by BMH, can be deleted or moved in a special folder, you have to define.
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


#### Maintenance
This module has a maintain function, which can repair several faults in the data.


#### Import
You can import data with various plug-ins:
- csv
- module rmbulletin
- module smartpartner
- module weblinks
- module evennews
- module subscribers
- users from xoops users
 
The import tool works in this way:
- Adding email to the list of subscribers
- Subscribe this email to one newsletter cat

Before you run import tool therefore, please create first minimum one newsletter cat, otherwise the email cannot be subscribed to a cat and the import fails.

You have the possibility
- to import the E-Mail-Addresses without any check (recommended for big import data sets) or
- after reading data you can decide for each email
-- whether you want to make a subscription or not
-- to which newsletter you want to make the subscription
If an email is already registered, import of this email should be skipped (default action, do not touch existing registrations). 
Sample files (sample1col.csv, sample4col.csv) for csv-import you can find in ../xnewsletter/plugins/ 

Attention:In case of registrations/subscription with this import tool there will not be sent an email notification to the email owner.


**Importation of big email lists:**

To avoid cache overflow during importation, there are two limits:
- first limit: only 100000 lines (e.g. of a csv-file) can be stored in temporary import table
- second limit: you can finally import data from temporary import table in packages of max. 25000

For import of more than 100k emails following procedure can be done:
- run first import email 1 to 100000 - import finally emails in packages of 25k - run second import emails 100001 to 200000 (select option "skip existing subscriptions") - import finally in packages of 25k and so on.
If file size is not too big to upload, you can repeat as often you want.


If you get somewhere a white page, it is no problem because if option "skip existing subscriptions" is selected the import procedure restart at the first not imported email-address.
Reduce number of importing emails or package size and try again.