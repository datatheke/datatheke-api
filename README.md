Datatheke-API
=============

About
-----
Documentation about the datatheke API

cURL exemples
-------------
*Note about security: all commands belows have the -k option to disable certificate verification*

## Token

### Get access token from user credentials
```sh
$> curl -k \
        -d 'grant_type=password&username=MY_USERNAME&password=MY_PASSWORD' \
        -X POST https://www.datatheke.com/api/v2/token
{"access_token":"XXXXXjc2NDllNzQ2M2UzN2FmYmRkZjcxMzJmYmIyOWMxM2ZkMTk1YjllNTAzZTY4ZTIxNzM2M2UyYTA4Mg","expires_in":3600,"token_type":"bearer","refresh_token"
:"XXXXXjE3NDkxMzU2NzE4OWI2NDI2ZmEyMTg1ZDE5NDZkNGZmN2ZiMDBjNzI4YmIxZDI0ZTg0YzY5MTE4Mw"}
```

### Refresh token
```sh
$> curl -k \
        -d 'grant_type=refresh_token&refresh_token=XXXXXjE3NDkxMzU2NzE4OWI2NDI2ZmEyMTg1ZDE5NDZkNGZmN2ZiMDBjNzI4YmIxZDI0ZTg0YzY5MTE4Mw' \
        -X POST https://www.datatheke.com/api/v2/token
{"access_token":"XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA","expires_in":3600,"token_type":"bearer","refresh_token"
:"XXXXjdmNjBkOWVmMmM5ZTM0MjAxYWZjZjQ1Y2I0ODhkZGEwZjlhNzM3YzE2YTA1MzZiZTY0N2YxMDcyNDJkOQ"}
```

## List

### All your Libraries
```sh
$> curl -k \
        -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
        -X GET https://www.datatheke.com/api/v2/libraries
```

### A specific library
```sh
$> curl -k \
        -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
        -X GET https://www.datatheke.com/api/v2/libraries/50bdea5e138a762671000002
```

### Collections of a library
```sh
$> curl -k \
        -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
        -X GET https://www.datatheke.com/api/v2/libraries/50bdea5e138a762671000002/collections
```

### A specific collection
```sh
$> curl -k \
        -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
        -X GET https://www.datatheke.com/api/v2/collections/50bdea73138a769664000024
```

### Items of a collection
```sh
$> curl -k \
        -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
        -X GET https://www.datatheke.com/api/v2/collections/50bdea73138a769664000024/items
```