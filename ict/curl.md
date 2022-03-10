# cURL

Example from Avira/Norton VPN system:

```bash
curl -X POST \
-H 'Authorization: PASSWORD' \
-d '{"device_id": "USERNAME", "pubkey": "PUBLIC_KEY"}' \
https://SERVER_ADDRESS:8443/v1/wg/auth
```

[-X](https://curl.se/docs/manpage.html#-X)

[-H](https://curl.se/docs/manpage.html#-H)

[-d](https://curl.se/docs/manpage.html#-d) sends the specified data in a POST request to the HTTP server, in the same way that a browser does when a user has filled in an HTML form and presses the submit button. This will cause curl to pass the data to the server using the content-type application/x-www-form-urlencoded.

Translating:

```
curl --location --request POST 'https://SERVER_ADDRESS:8443/v1/wg/auth' \
--header 'Authorization: PASSWORD' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'device_id=USERNAME' \
--data-urlencode 'pubkey=PUBLIC_KEY'
```

<details>

<summary>Spoiler alert</summary>

The above request won't work, the documentation was in error, use JSON

```bash
curl --location --request POST 'https://SERVER_ADDRESS:8443/v1/wg/auth' \
--header 'Authorization: PASSWORD' \
--header 'Content-Type: application/json' \
--data-raw '{
    "device_id": "USERNAME",
    "pubkey": "PUBLIC_KEY"
}'
```

</details>
