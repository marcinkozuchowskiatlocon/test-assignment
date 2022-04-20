# Test assignment

## The assessment will be based on following criteria:
- Java Knowledge
- Reuse of code
- Maintainability
- Ability to test
- Coding style

Write an application (a RESTful service) that implements a simple version of serving bookstore. A "Book" have the attributes [id:String, title:String, author:String]

We would like to see:
A web application client that calls REST API and handles all possible errors.
The client should be able to add, list, view and delete books.

A bookstore server that can serve a REST-service according to the Swagger-specification below.
That is:
- List all books
- Create a book
- Get one book by id
- Delete one book by id

## The REST service should support the following resources (can be viewed in editor.swagger.io)
```
swagger: "2.0"
info:
  description: "The definition of the API for Locon test assignment"
  version: "1.0.0"
  title: "Simple bookstore API"
host: "localhost:8080"
basePath: "/bookstore-web"
schemes:
- "http"
paths:
  /book:
    get:
      tags:
      - "book"
      summary: "Get all books"
      description: "Returns all books"
      operationId: "getAllBooks"
      produces:
      - "application/xml"
      - "application/json"
      responses:
        200:
          description: "successful operation"
          schema:
            $ref: "#/definitions/Book"
    post:
      tags:
      - "book"
      summary: "Add a new book"
      description: ""
      operationId: "addBook"
      consumes:
      - "application/json"
      - "application/xml"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
        - in: "body"
          name: "body"
          description: "Book object that needs to be stored in database"
          required: true
          schema:
            $ref: "#/definitions/Book"
      responses:
        201:
          description: "OK"
          schema:
            $ref: "#/definitions/Book"
        422:
          description: "Invalid input"
    put:
      tags:
      - "book"
      summary: "Updates a book"
      description: ""
      operationId: "updateBook"
      consumes:
      - "application/json"
      - "application/xml"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
        - in: "body"
          name: "body"
          description: "Book object that needs to be updated"
          required: true
          schema:
            $ref: "#/definitions/Book"
      responses:
        201:
          description: "OK"
          schema:
            $ref: "#/definitions/Book"
        404:
          description: "Book not found"
        422:
          description: "Invalid input"
  /book/{bookId}:
    get:
      tags:
      - "book"
      summary: "Find book by ID"
      description: "Returns a single book"
      operationId: "getBookById"
      produces:
      - "application/xml"
      - "application/json"
      parameters:
      - name: "bookId"
        in: "path"
        description: "ID of book to return"
        required: true
        type: "string"
      responses:
        200:
          description: "successful operation"
          schema:
            $ref: "#/definitions/Book"
        404:
         description: "Book not found"
    delete:
      tags:
      - "book"
      summary: "Deletes a book"
      description: ""
      operationId: "deleteBook"
      parameters:
        - name: "bookId"
          in: "path"
          description: "Book id to delete"
          required: true
          type: "string"
      responses:
        204:
          description: "successful operation"
        404:
          description: "Book not found"
definitions:
  Book:
    type: "object"
    required:
      - "title"
      - "author"
    properties:
      id:
        type: "string"
        example: "1"
      title:
        type: "string"
        example: "Thinking in Java"
      author:
        type: "string"
        example: "Bruce Eckel"
```

## Technical requirements
- as a dependency manager use maven
- to write the application use Spring

As a result send the repository address to us, e.g. on github
