# Operating Instructions

## Basic information

The module is based on PHPMailer and PHPMailer-BMH

## \(Un\) subscriptions to newsletters

You can define for each group, whether for \(un\) subscription or change a confirmation email with activation key is necessary or not \(use double-opt-in\).

## Create a newsletter

The newsletter can be created with each text editor which is installed in current xoops core \(e.g. TinyMCE\). For each newsletter you can use different templates \(see also 'Newsletter templates'\). You can define one or more newsletter categories for your newsletter. You can add 5 files maximum as attachment to each newsletter.

Optionally you can also copy an older newsletter and edit or send it as a new one.

The type of text editor, allows mime-types and size of mail attachments can be set in module preferences.

## Newsletter templates

The newsletters are template based. The templates are stored as files in language/{yourlanguage}/templates or stored in database. To create a new template you can:

* make a new template html-file in in language/{yourlanguage}/templates folder and to put in the smarty-vars;
* from admin side create a new template item and to put in the smarty-vars.

This module uses the XOOPS [Smarty template engine](http://www.smarty.net/) to render the email letter.

Available smarty-vars are:

* &lt;{$salutation}&gt; or &lt;{$sex}&gt;: the subscriber Salutation field
* &lt;{$firstname}&gt;: the subscriber First name field
* &lt;{$lastname}&gt;: the subscriber Last name field
* &lt;{$email}&gt; or &lt;{$subscr\_email}&gt;: the subscriber Email field
* &lt;{$title}&gt;: the newsletter Title field
* &lt;{$content}&gt;: the newsletter Content field
* &lt;{$date}&gt;: the sending date as timestamp integer  
 

  \(e.g.: &lt;{$date\|date\_format:"%Y/%m/%d"}&gt; will output the date formatted as 2001/01/04\)

* &lt;{$unsubscribe\_url}&gt;: the unsubscribe url
* &lt;{$xoops\_url}&gt;: the site main url \(e.g. [http://localhost/](http://localhost/)\)
* &lt;{$xoops\_langcode}&gt;: the site langcode \(e.g. en\)
* &lt;{$xoops\_charset}&gt;: the site charset \(e.g. UTF-8\)

## Sending newsletter

You can show a preview of a newsletter before sending. You can send the newsletter for testing to a defined email-address. The newsletters will be sent subscriber by subscriber. For each sending action a protocol will be created. If one or more send failed, you can see it in the protocol. You can restart sending procedure. You can send it again to all subscribers or send it only to the subscribers, where sending procedure failed.

You can send all emails immediately or limit emails send in one package. The number of emails and the minutes until next sending can be defined in module preferences \(e.g. 200 emails all 60 minutes\). The first package will be sent immediately. To start the next sending procedure you need an external cronjob, which is calling "../modules/xnewsletter/cron.php". Xoops cannot do this with current version \(2.5.5\).

Pay attention: functions like testing account, sending emails, start Bounced email handler,... work not with local server \(you get white page\).

## Task list

If you limit emails send in one package, you can see all newsletters waiting for next cronjob and the time, when cronjob can send the newsletter. If you do not use this option, the tab "Task list" is hidden.

## Handle mailing lists

If you have an existing mailing list, you can synchronize the \(un\) subscriptions of one newsletter category with one mailing list. I use majordomo beside this newsletter module because then I can also send an email from my email-client to the newsletter recipients. One of the disadvantages of mailing lists is, that, if one person is registered in two or more mailing lists and you send a one newsletter to all mailing lists, this person gets the same newsletter more than one time. With xnewsletter he gets only one newsletter.

Normally the tab "Mailing list" is hidden, if this option is disabled.

> ![](.gitbook/assets/important%20%283%29.png) **IMPORTANT:** xnewsletter cannot create mailing lists.

## Bounced email handler \(BMH\)

If you send newsletters, there will always be some emails not delivered to recipient \(Bounced email\), because email is no more valid, mailbox is full, and so on. To handle this event and to react on this, you can use BMH. You can activate BMH for each account. Mails, which are detected as Bounced emails by BMH, can be deleted or moved in a special folder, you have to define. Possible actions for Bounced emails: -- no action \(only store\) -- quit temporary the subscriptions of this email-address -- delete the subscriptions of this email-address

## Maintenance

This module has a maintain function, which can repair several faults in the data.

## Import

You can import data from other newsletter modules with various plug-ins.

