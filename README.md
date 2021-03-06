# Yammer Integration Pack

This integration pack allows you to integrate with
[Yammer](http://yammer.com/),
the Enterprise Social Network.

## Actions

The following actions are supported:

* `authenticate` - Get an authentication URL for the application, use this in a browser to gain a code. Put this code in `/opt/stackstorm/configs/yammer.yaml`
* `delete_group` - Removing a group
* `delete_message` - Remove a message
* `email_message` - Send the contents of a message to yourself
* `get_group_by_id` - Fetch the group details by ID
* `get_user_by_email` - Fetch a user by email
* `get_user_by_id` - Fetch a user by id
* `list_groups` - Get all groups
* `list_messages` - List all messages
* `list_messages_in_group` - List all messages in a group
* `list_messages_about_topic` - List all messages about a particular topic
* `list_messages_from_user` - List all messages from a particular user
* `list_messages_my_feed` - List messages for my feed
* `list_private_messages` - List the messages in your inbox
* `list_users`
* `list_users_in_group`
* `like_message` - Like a particular message
* `post_message` - Post a message to a user, a group or a topic
* `suspend_user` - Suspend a user (admins only)

## Configuration

In Yammer you need to setup a client application on (https://www.yammer.com/client_applications).

Copy the example configuration in [yammer.yaml.example](./yammer.yaml.example)
to `/opt/stackstorm/configs/yammer.yaml` and edit as required, using values from Yammer.

Configure these values:

* `client_id` - The client ID provided by Yammer for your app
* `client_secret` - The client secret provided by Yammer for your app
* `expected_redirect` - The redirect Yammer expects to send you to, configured below.

Once those values have been configured, register the configuration with `sudo st2ctl reload --register-configs`,
then run the `authenticate` action. This will give you a URL. Navigate to that URL
in a browser and login to Yammer.

This will give you an access code. Configure this in `yammer.yaml`:

* `access_code` - The code generated by viewing the URL provided when running `authenticate`

Run `sudo st2ctl reload --register-configs` again, and you can use the rest of the integration
