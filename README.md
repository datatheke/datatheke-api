Datatheke-API
=============

About
-----
Documentation about the datatheke API

cURL exemples
-------------
*Note about security: all commands belows have the -k option to disable certificate verification*

# Token

## Get access token from user credentials
```sh
$> curl -k \
        -d 'grant_type=password&username=MY_USERNAME&password=MY_PASSWORD' \
        -X POST https://www.datatheke.com/api/v2/token
{"access_token":"XXXXXjc2NDllNzQ2M2UzN2FmYmRkZjcxMzJmYmIyOWMxM2ZkMTk1YjllNTAzZTY4ZTIxNzM2M2UyYTA4Mg","expires_in":3600,"token_type":"bearer","refresh_token"
:"XXXXXjE3NDkxMzU2NzE4OWI2NDI2ZmEyMTg1ZDE5NDZkNGZmN2ZiMDBjNzI4YmIxZDI0ZTg0YzY5MTE4Mw"}
```