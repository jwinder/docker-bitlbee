docker-bitlbee
==============

## Logging in

To run bitlbee:

`docker run -d -p 6667:6667 -v $HOME/bitlbee-data/:/var/lib/bitlbee/ jwinder/bitlbee`

Then connect with your IRC client: `localhost:6667` and switch to the `&bitlbee` irc channel. This is the control channel where you interact with bitlbee, as well as talking to contacts to creating irc rooms for contacts or group chats.

To login for the first time (without the brackets): `register <your-new-password>`. All following times: `identify <your-new-password>`.

## Common commands

- `help` and `help commands` display useful commands listings
- `account list` displays all registered accounts (can be shortened, e.g. `acc li`)
- `blist` displays all users (can be shortened: e.g. `bli`)
- `account <name> set tag <new-name>` renames an account
- `plugins` for a list of supported protocols
- `help purple` for a list of libpurple supported protocols
- `save` to save the current configuration (sometimes after changing account names, it doesn't autosave)

## Twitter

`account add twitter <username>`

`account twitter on`

A new irc channel will display a twitter link to follow for authorizing your application. After authorizing bitlbee for twitter, twitter will display a code. Send this code to the temporary irc channel. Bitlbee will now be authorized to use twitter.

## Facebook

Create an app password for bitlbee [here](https://www.facebook.com/settings?tab=security&section=per_app_passwords).

`account add facebook <email> <app-password>`

`account facebook on`

## Google Hangouts

`account add hangouts <email>`

`account hangouts on`

A new irc channel will guide you through retrieving an oauth token for bitlbee to use. The gist is: if you are already logged into google, go [here](https://accounts.google.com/o/oauth2/programmatic_auth?hl=en&scope=https%3A%2F%2Fwww.google.com%2Faccounts%2FOAuthLogin+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email&client_id=936475272427.apps.googleusercontent.com&access_type=offline&delegated_client_id=183697946088-m3jnlsqshjhh5lbvg05k46q1k4qqtrgn.apps.googleusercontent.com&top_level_cookie=1). Inspect the cookies for an `oauth_token` cookie. Copy the value of the cookie into the irc channel. Bitlbee will now be authorized to use hangouts.

The following setting will also help with showing full names for contacts: `account hangouts set nick_format %full_name` and `save`
