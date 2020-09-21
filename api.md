# Recipe Store API

This document will detail the behavior of the backend API for the recipe store project, including all available
endpoints, the HTTP method used to access them, a description of what they accept

## Authentication

Initially, authentication will be accomplished via OAuth. It will use passport.js to accomplish this.

### `login` - `POST`

### `logout` - `POST`

## Search

Like any good website, there should be search functionality. This will take the search term and compare it with various
keywords in the stored recipes.

### `search` - `GET`

This endpoint accepts a `string` for the search. It then returns a paginated list containing the following properties:

* `title` - `string`
* `author` - `string`
* `image` - `string` - base64 string
* `description` - `string` - optional description of recipe
* `id` - `uuid` - document identifier for quick lookup

## Load

This endpoint will allow a user to load a recipe based on the recipe's identifier.

### `load` - `GET`

This endpoint accepts a `uuid`. It then returns a `Recipe`.

## Save and Update

This endpoint will allow a user to add a new recipe or update an existing recipe.

### `insert` - `POST`

This endpoint accepts a `NewRecipe` object and stores it in the database. It then returns the
identifier of the inserted recipe.

### `update` - `PUT`

This endpoint accepts a `Recipe` object. It updates the record in the database and returns a
status.

### `delete` - `DELETE`

This endpoint accepts a `uuid`. It deletes the record in the database matching that identifier.

## Models

### `NewRecipe`

A `NewRecipe` model will be defined as follows:

* `title` - `string`
* `author` - `string`
* `published` - `date`
* `recipe` - `string` - full recipe as markdown
* `updated` - `date` - optional
* `image` - `string` - optional base64 string
* `description` - `string` - optional description of recipe
* `url` - `string` - optional URL where original recipe can be located

### `Recipe`

A `Recipe` model will extend a `NewRecipe`, adding the following property:

* `id` - `uuid`