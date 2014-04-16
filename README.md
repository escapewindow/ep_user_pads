# ep_user_pads

User Pads Plugin for EtherPad Lite

This is a merge of two interdependent plugins: [ep_user_pad](https://github.com/vltugraz/ep_user_pad) and [ep_user_pad_frontend](https://github.com/vltugraz/ep_user_pad_frontend).

## Installation
You can clone directly into the node_modules directory of your Etherpad installation. 

`git clone https://github.com/vltugraz/ep_user_pads.git`

If you do that, you can follow this procedure after that:

1. `cd ep_user_pads`
2. `npm install`
3. rename email.json.template to email.json
4. enter correct data in email.json (see email.json section)
5. restart etherpad

Dont forget to create the database tables at some point if not already present or migrate from previous versions.

## Migration
There has been a database transformation which includes:
* changed column names
* changed primary keys
* introduced constraints (foreign keys)

All database changes are possible on a existing installation and can be automated using the provided [migrate_tables.sql](sql/migrate_tables.sql) file. Please be aware that all rows violating foreign constraints will be deleted. In our migration of a 4GB database, ZERO rows were deleted.

## email.json

This file contains all the settings for this plugin. See the table below for the explanation of every setting.

| Name | Value | explanation |
| :------------ | :---------------: | :----- |
| smtp | boolean | Is the setting ’true’, the plugin uses a smtp - server to sent the messages Is this Value false the mail will be send over the server on port 25. The settings ’user’ to ’ssl’ are not necessary if this setting is false. |
| user | string | Name of the smtp-user. |
| password | string | Password of the smtp-user. |
| host | string | Hostname of the smtp-server. |
| port | int | Port of the smtp-server. |
| tls | boolean | Is this value ’true’ the message is encrypted with tls. |
| ssl | boolean | Is this value ’true’ the message is encrypted with ssl. |
| invationsmsg | string | Message of the E-Mail which will be sent if a user was added to a group. The variables \<fromuser\> (sender of the message), \<groupname\> (name of the group where the user is invited to) and \<url\> (Homepage of the application) can be included in the text and will be replaced by the plugin. |
| invationfrom | string | Sender of the e-mail which will be sent if a user was added to a group. |
| invitationsubject | string | Subject of the e-mail which will be sent if a user was added to a group. |
| registrationtext | string | Message of the E-Mail which will be sent if a user has registered. The variable \<url\> (Homepage of the application) can be included in the text and will be replaced by the plugin. |
| registrationfrom | string | Sender of the e-mail which will be sent if a user has registered. |
| registrationsubject | string | Subject of the e-mail which will be sent if a user has registered. |
| invitateunregisterednmsg | string | The text of an e-mail which is sent if a person was invited to a group but this person is not yet registered at the application. The variables \<fromuser\> (sender of the message), \<groupname\> (name of the group where the user is invited to) and \<url\> (Homepage of the application) can be included in the text and will be replaced by the plugin. |