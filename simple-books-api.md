# Simple Books API 📚 📚  #

This API allows you to reserve a book.

The API is available at `https://simple-books-api.glitch.me`

## Endpoints ##

### 1. Status ###

```diff
+ GET
```  

 `/status`

Returns the status of the API.

### 2. List of books ###

```diff
+ GET
``` 

`/books`

Returns a list of books.

🟩 Optional query parameters:

- type: fiction or non-fiction
- limit: a number between 1 and 20.


### 3. Get a single book ###

```diff
+ GET
``` 
`/books/:bookId`

Retrieve detailed information about a book.


### 4. Submit an order ###
```diff
! POST
``` 

 `/orders`

Allows you to submit a new order. [Requires authentication](https://github.com/EiderDiaz/introduction-to-postman-course/blob/main/simple-books-api.md#9-api-authentication).

🟧 The request body needs to be in JSON format and include the following properties:

 - `bookId` - Integer - Required
 - `customerName` - String - Required

Example
```json
POST /orders/
Authorization: Bearer <YOUR TOKEN>

{
  "bookId": 1,
  "customerName": "John"
}
```

The response body will contain the order Id.

### 5. Get all orders ###

```diff
+ GET
``` 

 `/orders`

Allows you to view all orders. [Requires authentication](https://github.com/EiderDiaz/introduction-to-postman-course/blob/main/simple-books-api.md#9-api-authentication).

### 6. Get an order ###

```diff
+ GET
``` 
`/orders/:orderId`

Allows you to view an existing order. [Requires authentication](https://github.com/EiderDiaz/introduction-to-postman-course/blob/main/simple-books-api.md#9-api-authentication).

### 7. Update an order ###

```diff
@@ PATCH @@
```

 `/orders/:orderId`

Update an existing order. [Requires authentication](https://github.com/EiderDiaz/introduction-to-postman-course/blob/main/simple-books-api.md#9-api-authentication).

🟪 The request body needs to be in JSON format and allows you to update the following properties:

 - `customerName` - String

 Example
```
PATCH /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>

{
  "customerName": "John"
}
```

### 8. Delete an order ###

```diff
- DELETE
```

 `/orders/:orderId`

Delete an existing order. [Requires authentication](https://github.com/EiderDiaz/introduction-to-postman-course/blob/main/simple-books-api.md#9-api-authentication).

The request body needs to be empty.

 Example
```json
DELETE /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>
```

## 9. API Authentication ##

To submit or view an order, you need to register your API client.

```diff
! POST
```

 `/api-clients/`

🟧 The request body needs to be in JSON format and include the following properties:

 - `clientName` - String
 - `clientEmail` - String

 Example

 ```json
 {
    "clientName": "Postman",
    "clientEmail": "valentin@example.com"
}
 ```

The response body will contain the access token. The access token is valid for 7 days.

**Possible errors**

Status code 409 - "API client already registered." Try changing the values for `clientEmail` and `clientName` to something else.
