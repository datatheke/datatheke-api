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
     -d 'grant_type=password&username={USERNAME}&password={PASSWORD}' \
     -X POST https://www.datatheke.com/api/v2/token
{"access_token":"XXXXXjc2NDllNzQ2M2UzN2FmYmRkZjcxMzJmYmIyOWMxM2ZkMTk1YjllNTAzZTY4ZTIxNzM2M2UyYTA4Mg","expires_in":3600,"token_type":"bearer","refresh_token"
:"XXXXXjE3NDkxMzU2NzE4OWI2NDI2ZmEyMTg1ZDE5NDZkNGZmN2ZiMDBjNzI4YmIxZDI0ZTg0YzY5MTE4Mw"}
```

### Refresh token
```sh
curl -k \
     -d 'grant_type=refresh_token&refresh_token={REFRESH_TOKEN}' \
     -X POST https://www.datatheke.com/api/v2/token
{"access_token":"XXXXXTFkOTdiZmI3NTBkYTA2ODY3Y2ZiZDYyMjYzYjZkZWFjNGY3OGNjY2JmOTI2N2IxODlhYWNhMDRkMTk2NA","expires_in":3600,"token_type":"bearer","refresh_token"
:"XXXXjdmNjBkOWVmMmM5ZTM0MjAxYWZjZjQ1Y2I0ODhkZGEwZjlhNzM3YzE2YTA1MzZiZTY0N2YxMDcyNDJkOQ"}
```

## List
Note: Each call will return 20 rows maximum. You can add a parameter '?page=PAGE_NUMBER' to get the next ones

### All your Libraries
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -X GET https://www.datatheke.com/api/v2/libraries
```

### A specific library
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -X GET https://www.datatheke.com/api/v2/libraries/{LIBRARY_ID}
```

### Collections of a library
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -X GET https://www.datatheke.com/api/v2/libraries/{LIBRARY_ID}/collections
```

### A specific collection
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -X GET https://www.datatheke.com/api/v2/collections/{COLLECTION_ID}
```

### Items of a collection
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -X GET https://www.datatheke.com/api/v2/collections/{COLLECTION_ID}/items
```

### An item
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -X GET https://www.datatheke.com/api/v2/collections/{COLLECTION_ID}/items/{ITEM_ID}
```

## Create
Note: add '.xml' to the URL to get XML response

### A library
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -H "Content-type: application/json" \
     -d '{"name": "My brand new library", "description": "Exemple for the API documentation"}' \
     -X POST https://www.datatheke.com/api/v2/libraries
```

### A collection
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -H "Content-type: application/json" \
     -d '{"name": "This is a test", "fields": [{"label": "Username", "type": "string"}, {"label": "Birthdate", "type": "date"}]}' \
     -X POST https://www.datatheke.com/api/v2/libraries/{LIBRARY_ID}
```

### An item
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -H "Content-type: application/json" \
     -d '{"_{FIELD_1_ID}": "Bob Marley", "_{FIELD_2_ID}": "06/02/1945"}' \
     -X POST https://www.datatheke.com/api/v2/collections/{COLLECTION_ID}
```

## Update
Note: add '.xml' to the URL to get XML response

### A library
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -H "Content-type: application/json" \
     -d '{"name": "Updated library", "description": "Updated description"}' \
     -X PUT https://www.datatheke.com/api/v2/libraries/{LIBRARY_ID}
```

### A collection
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -H "Content-type: application/json" \
     -d '{"name": "Updated collection", "fields": [{"label": "Singer"}, {"label": "Birthdate"}]}' \
     -X PUT https://www.datatheke.com/api/v2/collections/{COLLECTION_ID}
```

### An item
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -H "Content-type: application/json" \
     -d '{"_{FIELD_1_ID}": "Frank Sinatra", "_{FIELD_2_ID}": "12/12/1915"}' \
     -X PUT https://www.datatheke.com/api/v2/collections/{COLLECTION_ID}/items/{ITEM_ID}
```

### Delete
Note: add '.xml' to the URL to get XML response

### A library
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -X DELETE https://www.datatheke.com/api/v2/libraries/{LIBRARY_ID}
```

### A collection
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -X DELETE https://www.datatheke.com/api/v2/collections/{COLLECTION_ID}
```

### An item
```sh
curl -k \
     -H "Authorization: Bearer {ACCESS_TOKEN}" \
     -X DELETE https://www.datatheke.com/api/v2/collections/{COLLECTION_ID}/items/{ITEM_ID}
```
