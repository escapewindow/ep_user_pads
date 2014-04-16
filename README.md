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

## Migration
There has been a database transformation which includes:
* changed column names
* changed primary keys
* introduced constraints (foreign keys)

All database changes are possible on a existing installation and can be automated using the provided [migrate_tables.sql](sql/migrate_tables.sql) file. Please be aware that all rows violating foreign constraints will be deleted. In our migration of a 4GB database, ZERO rows were deleted.

