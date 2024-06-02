### POST/PUT/PATCH APIs of books, categories will return 403 FORBIDDEN if a USER tried to call these APIs. ONLY ADMIN can call POST/PUT/PATCH on books, categories
### ADMIN cannot POST a rent - which will result to a 403 FORBIDDEN. ONLY USER can create a rent
## Renting API

| Method | Route     | Input                                                           | Output _____________________                          | Error                                          | Description              
|--------|-----------|-----------------------------------------------------------------|-------------------------------------------------------|------------------------------------------------|--------------------------|
| POST   | /api/rent | {<br>"userId": Long,<br>"bookId": Long,<br>"endDate": Date<br>} | "Book rented successfully!" <br> - *HTTP Status: 200* | 400 BAD REQUEST AND 403 FORBIDDEN WITH MESSAGE | Only user can rent books |

## Auth API

| Method | Route              | Input                                               | Output __________________                                                                                  | Error                        | Description   
|--------|--------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------|------------------------------|---------------|
| POST   | /api/auth/register | {<br>"username": String<br>"password": String <br>} | "User registered" <br> - *HTTP Status: 200*                                                                | 400 BAD REQUEST WITH MESSAGE | User register |
| POST   | /api/auth/login    | {<br>"username": String<br>"password": String <br>} | {<br>"accessToken": Token <br> "tokenType": "Bearer " <br> "message": "Success" <br>} - *HTTP Status: 200* | 400 BAD REQUEST WITH MESSAGE | User login    |

## Book API

| Method | Route          | Input ___________                                   | Output __________________ | Error                                                        | Description            
|--------|----------------|-----------------------------------------------------|---------------------------|--------------------------------------------------------------|------------------------|
| GET    | /api/books     |                                                     | List of books             |                                                              | Get all books          |
| GET    | /api/books/:id |                                                     | One book                  | 404 NOT FOUND WITH MESSAGE                                   | Get a book             |
| POST   | /api/books     | {<br> "name" : String <br> "categoryId": Long <br>} | Persisted book            | 400 BAD REQUEST WITH MESSAGE                                 | Persist a book         |
| PUT    | /api/books/:id | {<br> "name" : String <br> "categoryId": Long <br>} | Updated book              | 400 BAD REQUEST WITH MESSAGE <br> 404 NOT FOUND WITH MESSAGE | Update a book          |
| PATCH  | /api/books/:id | {<br> "quantity": Long <br>}                        | Added quantity book       | 400 BAD REQUEST WITH MESSAGE                                 | Add quantity to a book |

## Categories API - generated by Spring Data REST

| Method | Route               | Input ___________           | Output __________________ | Error                      | Description                                                             
|--------|---------------------|-----------------------------|---------------------------|----------------------------|-------------------------------------------------------------------------|
| GET    | /api/categories     |                             | List of categories        |                            | Get all categories                                                      |
| GET    | /api/categories/:id |                             | One category              | 404 NOT FOUND WITH MESSAGE | Get a category                                                          |
| POST   | /api/categories     | {<br> "name" : String <br>} | Persisted category        |                            | Persist a category                                                      |
| PUT    | /api/categories/:id | {<br> "name" : String <br>} | Updated category          |                            | Update a category - If ID not exists, Spring will create a new category |
