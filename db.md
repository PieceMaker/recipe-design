# Recipe Store Database

This document will detail the structure of the database that will be accessed via the recipe store API. It will include
all tables and what data will be stored in each table.

## Recipes

Recipes will be stored as JSON in a table called `recipes`. The JSON will contain the following properties:

* `title` - `string`
* `author` - `string`
* `published` - `date`
* `recipe` - `string` - full recipe as markdown
* `updated` - `date` - optional
* `image` - `string` - optional base64 string
* `description` - `string` - optional description of recipe
* `url` - `string` - optional URL where original recipe can be located