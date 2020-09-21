# Recipe Store API

This document will detail the behavior of the backend API for the recipe store project, including all available
endpoints, the HTTP method used to access them, a description of what they accept

## Authentication

Initially, authentication will be accomplished via OAuth. It will use passport.js to accomplish this.

### `/login` - `POST`

### `/logout` - `POST`

## Search

Like any good website, there should be search functionality. This will take the search term and compare it with various
keywords in the stored recipes.

### `/search/{pattern}/{page?}` - `GET`

* `pattern` - `string`
* `page` - `integer` - optional

Returns a paginated `SummaryRecipe[]`. If `page` is not specified, defaults to `page = 1`.

## Load

This endpoint will allow a user to load a recipe based on the recipe's identifier.

### `/load/{id}` - `GET`

* `id` - `uuid` - Identifier of the document to load.

Returns a `Recipe`.

## Write

This endpoint will allow a user to add a new recipe or update an existing recipe.

### `/insert` - `POST`

Accepts a `NewRecipe` object and stores it in the database. It then returns the identifier
of the inserted recipe.

### `/update/{id}` - `PUT`

* `id` - `uuid` - Identifier of the document to update.

This endpoint accepts a `Recipe` object. It updates the record in the database and returns a
status.

### `/delete/{id}` - `DELETE`

* `id` - `uuid` - Identifier of the document to update

Deletes the record in the database matching that identifier.

## Models

### `BaseRecipe`

* `title` - `string`
* `author` - `string`
* `image` - `string` - base64 string
* `description` - `string` - optional description of recipe

### `NewRecipe`

A `NewRecipe` model will be defined as follows:

* `published` - `date`
* `recipe` - `string` - full recipe as markdown
* `updated` - `date` - optional
* `url` - `string` - optional URL where original recipe can be located

### `Recipe`

A `Recipe` model will extend a `NewRecipe`, adding the following property:

* `id` - `uuid`

### `SummaryRecipe`

A `SummaryRecipe` model extends a `BaseRecipe`, adding the following property:

* `id` - `uuid` - document identifier for quick lookup