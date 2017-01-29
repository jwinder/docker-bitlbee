docker-bitlbee
==============

![](https://img.shields.io/docker/automated/jwinder/docker-bitlbee.svg)

- https://bitlbee.org
- https://hub.docker.com/r/jwinder/docker-bitlbee

## Logging in

To run bitlbee:

- `docker run -d -p 6667:6667 -v $HOME/.bitlbee/:/var/lib/bitlbee/ jwinder/docker-bitlbee`

Then connect to `localhost:6667` with an irc client and switch to the `&bitlbee` channel. This is the control channel where you will interact with bitlbee.

Make up some random password. To login for the first time (without the brackets):

- `register <some-password>`

All following times:

- `identify <some-password>`

## Common commands

- `help` and `help commands` display useful commands listings
- `account list` displays all registered accounts (can be shortened, e.g. `acc li`)
- `blist` or `/names` displays all contacts (can be shortened e.g. `bli`)
- `plugins` for a list of supported protocols
- `help purple` for a list of libpurple supported protocols
- `save` to save the current configuration (sometimes after adding/changing accounts, it doesn't save right away)
- `account <name> set tag <new-name>` renames an account
- `account <name> set auto_connect off` to turn off autoconnect for a specific account on login
- `chan &bitlbee set show_users online+,away+,offline` to show more than online contacts for `/names`

## Chatting

You can private message a nick `/msg <nick> <msg>` from the control channel. Within reason, you can invite others to these rooms as well, creating a group chat: `/invite <nick>`.

You can also talk to a nick directly in the control channel. Type a contact's name and direct a message to them just like any irc channel with multiple people: `<nick>: <msg>`. Their response will be in the control channel.

## Twitter

- `account add twitter <username>`
- `account twitter on`

Bitlbee will open a private chat with you, sending a twitter link to follow for authorizing bitlbee. Accept the terms, then twitter will display a code. Reply with this code in the private chat. Bitlbee will now be authorized to use twitter. Don't forget to `save`.

Bitlbee will automatically open a private irc channel to the twitter contact containing recent tweets in your feed.

Sending a message to the twitter contact in the control channel as well as inside of the private twitter irc channel will both post tweets, so be careful.

Sending a private message to a twitter user via `/msg <nick> <msg>` will send that user a twitter DM, not a tweet.

## Facebook

Create an app password for bitlbee [here](https://www.facebook.com/settings?tab=security&section=per_app_passwords).

- `account add facebook <email> <app-password>`
- `account facebook on`
- `save`

## Google Hangouts

- `account add hangouts <email>`
- `account hangouts set nick_format %full_name`
- `account hangouts on`

Bitlbee will open a private chat with you, sending instructions for retrieving an oauth token from google. The gist is: if you are already logged into google, go [here](https://accounts.google.com/o/oauth2/programmatic_auth?hl=en&scope=https%3A%2F%2Fwww.google.com%2Faccounts%2FOAuthLogin+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email&client_id=936475272427.apps.googleusercontent.com&access_type=offline&delegated_client_id=183697946088-m3jnlsqshjhh5lbvg05k46q1k4qqtrgn.apps.googleusercontent.com&top_level_cookie=1). Inspect the cookies for an `oauth_token` cookie. Reply with the value of this cookie in the private chat. Bitlbee will now be configured to use hangouts.

Don't forget to `save`.
