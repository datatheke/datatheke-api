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
curl -k \
     -d 'grant_type=password&username=MY_USERNAME&password=MY_PASSWORD' \
     -X POST https://www.datatheke.com/api/v2/token
{"access_token":"XXXXXjc2NDllNzQ2M2UzN2FmYmRkZjcxMzJmYmIyOWMxM2ZkMTk1YjllNTAzZTY4ZTIxNzM2M2UyYTA4Mg","expires_in":3600,"token_type":"bearer","refresh_token"
:"XXXXXjE3NDkxMzU2NzE4OWI2NDI2ZmEyMTg1ZDE5NDZkNGZmN2ZiMDBjNzI4YmIxZDI0ZTg0YzY5MTE4Mw"}
```

### Refresh token
```sh
curl -k \
     -d 'grant_type=refresh_token&refresh_token=XXXXXjE3NDkxMzU2NzE4OWI2NDI2ZmEyMTg1ZDE5NDZkNGZmN2ZiMDBjNzI4YmIxZDI0ZTg0YzY5MTE4Mw' \
     -X POST https://www.datatheke.com/api/v2/token
{"access_token":"XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA","expires_in":3600,"token_type":"bearer","refresh_token"
:"XXXXjdmNjBkOWVmMmM5ZTM0MjAxYWZjZjQ1Y2I0ODhkZGEwZjlhNzM3YzE2YTA1MzZiZTY0N2YxMDcyNDJkOQ"}
```

## List
Note: Each call will return 20 rows maximum. You can add a parameter '?page=PAGE_NUMBER' to get the next ones

### All your Libraries
```sh
curl -k \
     -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
     -X GET https://www.datatheke.com/api/v2/libraries
```

### A specific library
```sh
curl -k \
     -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
     -X GET https://www.datatheke.com/api/v2/libraries/50bdea5e138a762671000002
```

### Collections of a library
```sh
curl -k \
     -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
     -X GET https://www.datatheke.com/api/v2/libraries/50bdea5e138a762671000002/collections
```

### A specific collection
```sh
curl -k \
     -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
     -X GET https://www.datatheke.com/api/v2/collections/50bdea73138a769664000024
```

### Items of a collection
```sh
curl -k \
     -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
     -X GET https://www.datatheke.com/api/v2/collections/50bdea73138a769664000024/items
```

### An item
```sh
curl -k \
     -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
     -X GET https://www.datatheke.com/api/v2/collections/50bdea73138a769664000024/items/50bdea8c138a762671000003
```

## Create
Note: add '.xml' to the URL to get XML response

### A library
```sh
curl -k \
     -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
     -H "Content-type: application/json" \
     -d '{"name": "My brand new library", "description": Exemple for the API documentation"}' \
     -X POST https://www.datatheke.com/api/v2/libraries
```

### A collection
```sh
curl -k \
     -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
     -H "Content-type: application/json" \
     -d '{"name": "Collection de test2", "fields": [{"label": "Username", "type": "string"}, {"label": "Birthdate", "type": "date"}]}' \
     -X POST https://www.datatheke.com/api/v2/libraries/XXXXX
```

### An item
```sh
curl -k \
     -H "Authorization: Bearer XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA" \
     -H "Content-type: application/json" \
     -d '{"_53f734fbbb8556cc01000006": "Bob Marley", "_53f734fbbb8556cc01000007": "06/02/1945"}' \
     -X POST https://www.datatheke.com/api/v2/collections/XXXXX
```

## Update
Note: add '.xml' to the URL to get XML response

### A library
```sh
curl -k \
     -H "Authorization: Bearer OTcwOWY1MjdhZWY2NGU5ZTBhZDgzNzRjZGY2NTdjZDJhMmJkMjQ0MGQxYjE4MjdjYjIyOGNhZWQ4ZjA0MmYwNA" \
     -H "Content-type: application/json" \
     -d '{"name": "Updated library", "description": "Updated description"}' \
     -X PUT https://www.datatheke.com/api/v2/libraries
```

### A collection
```sh
curl -k \
     -H "Authorization: Bearer OTcwOWY1MjdhZWY2NGU5ZTBhZDgzNzRjZGY2NTdjZDJhMmJkMjQ0MGQxYjE4MjdjYjIyOGNhZWQ4ZjA0MmYwNA" \
     -H "Content-type: application/json" \
     -d '{"name": "Updated collection", "fields": [{"label": "Singer"}, {"label": "Birthdate"}]}' \
     -X PUT https://www.datatheke.com/api/v2/collections/XXXXX
```

### An item
```sh
curl -k \
     -H "Authorization: Bearer OTcwOWY1MjdhZWY2NGU5ZTBhZDgzNzRjZGY2NTdjZDJhMmJkMjQ0MGQxYjE4MjdjYjIyOGNhZWQ4ZjA0MmYwNA" \
     -H "Content-type: application/json" \
     -d '{"_53f734fbbb8556cc01000006": "Frank Sinatra", "_53f734fbbb8556cc01000007": "12/12/1915"}' \
     -X PUT https://www.datatheke.com/api/v2/collections/XXXXX/items/XXXXX
```

### Delete
Note: add '.xml' to the URL to get XML response

### A library
```sh
curl -k \
     -H "Authorization: Bearer OTcwOWY1MjdhZWY2NGU5ZTBhZDgzNzRjZGY2NTdjZDJhMmJkMjQ0MGQxYjE4MjdjYjIyOGNhZWQ4ZjA0MmYwNA" \
     -X DELETE https://www.datatheke.com/api/v2/libraries/XXXXX
```

### A collection
```sh
curl -k \
     -H "Authorization: Bearer OTcwOWY1MjdhZWY2NGU5ZTBhZDgzNzRjZGY2NTdjZDJhMmJkMjQ0MGQxYjE4MjdjYjIyOGNhZWQ4ZjA0MmYwNA" \
     -X DELETE https://www.datatheke.com/api/v2/collections/XXXXX
```

### An item
```sh
curl -k \
     -H "Authorization: Bearer OTcwOWY1MjdhZWY2NGU5ZTBhZDgzNzRjZGY2NTdjZDJhMmJkMjQ0MGQxYjE4MjdjYjIyOGNhZWQ4ZjA0MmYwNA" \
     -X DELETE https://www.datatheke.com/api/v2/collections/XXXXX/items/XXXXX
```