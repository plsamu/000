# Get list of Mastodon instances

## API

* https://mastodon.uno/api/v1/timelines/public
* https://mastodon.example/api/v1/accounts/:id
  * https://mastodon.uno/api/v1/accounts/1
* https://mastodon.example/api/v1/accounts/:id/followers
  * Authorization required - Bearer \<app token>

## Idea 1

* every x minute launch /timelines/public
* get user and their instance name
* get the name and get the followers
  * https://mastodon.uno/web/@\<ID>/followers
* save users and save the instances in a database

