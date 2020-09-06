# Recipe Store Client

This document will detail the behavior of the client for the recipe store project. It will discuss desired
functionality and how this functionality will interact with the recipe store API.

## Login

Because this content compiles works found around the internet, we want to ensure only authorized users can access the
content. As such, users must be provided a temporary account creation URL, they must then create an account, and they
must be logged in in order to access any of the content. Additionally, logout functionality must be provided so a user
can log out if they desire.

## Search

There should be a search bar where somebody can search for various keywords. This will call `/search` in the API.

## Front Page

The front page should display a couple of recipes. These should be either recent or random. They should display the
title, an image if it exists, and perhaps a short description or the beginning of the description.

## Recipe Page

When a recipe page is loaded, it will display the full recipe, including title, author, when it was published, and the
full recipe which will be parsed markdown. It will optionally display the following: when it was updated, an image, and
a description.

## Add and Modify Recipes

The client will provide the ability for users to add new recipes or modify existing recipes. There will be a button for
adding new recipes that will make a call to the `save` endpoint. When a recipe is loaded, there will be a button to
edit, which will make a call to the `update` endpoint.

Each of these endpoints will load a form containing the following:

* `title` - required
* `author` - required
* `recipe` - required
* `description` - optional
* `image` - optional
* `url` - optional URL where original recipe can be located