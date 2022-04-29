---
description: Have already other project, IDK why I am here
---

# Get list of Mastodon instances

## API

### Some API are public, like this:

* https://mastodon.uno/api/v1/timelines/public

### Get user info

* https://mastodon.example/api/v1/accounts/:id
  * https://mastodon.uno/api/v1/accounts/1

### Get all the follower of a user

* https://mastodon.example/api/v1/accounts/:id/followers
  * Authorization required - Bearer \<app token>
* https://mastodon.example/users/:username/followers?page=3
  * from page 1 to page n scrape all the user

## Idea 1

* every x minute launch /timelines/public
* get user and their instance name
* get the name and get the followers
  * https://mastodon.uno/web/@\<ID>/followers
* save users and save the instances in a database

