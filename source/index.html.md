---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Alexandria is a Headless CMS. With our API you can create blueprints(like posts, comments, products) and the blueprints can have items(like rows in a table).

# Create a Blueprint

## HTTP Request

```shell
curl https://api.alexandria.io/v1/blueprint \
-H `Content-Type: application/json` \
-d `{
        "key": "MY_KEY",
        "name": "Products",
        "fields": [{
          "type": "string",
          "name": "name"
        },{
          "type": "string",
          "name": "thumb_url"
        }, {
          "type": "string",
          "name": "img_large"
        },{
          "type": "number",
          "name": "price"
        }]
    }`
```

> Response (HTTP Status 200)

```json
{
  "id": "BLUEPRINT ID"
}
```

## Query Parameters

Name | Required | Type | Default | Description
---- | -------- | ---- | ------- | -----------
key | yes | string | | The API key
name | yes | string | | The blueprint name
fields | yes | array | | An array containing the blueprint fields(types available are string, boolean, number, array and object)

# Update a Blueprint

```shell
curl --request PUT https://api.alexandria.io/v1/blueprint/ID \
-H `Content-Type: application/json` \
-d `{
        "key": "MY_KEY",
        "name": "Products",
        "fields": [{
          "type": "string",
          "name": "name"
        },{
          "type": "string",
          "name": "thumb_url"
        }, {
          "type": "string",
          "name": "img_large"
        },{
          "type": "number",
          "name": "price"
        }]
    }`
```

> Response (HTTP Status 200)

```json
"OK"
```

## Query Parameters

Same as creating a blueprint.

# Delete a Blueprint

<aside class="notice">
If the blueprint has items, it can't be deleted until you delete all items.
</aside>

```shell
curl --request DELETE https://api.alexandria.io/v1/blueprint/ID \
-H `Content-Type: application/json` \
-d `{
        "key":"MY_KEY"
    }`
```

> Response

```json
"OK"
```

## Query Parameters

Name | Required | Type | Default | Description
---- | -------- | ---- | ------- | -----------
key | yes | string | | The API key

# List Blueprints

```shell
curl --request GET https://api.alexandria.io/v1/blueprints \
-H `Content-Type: application/json` \
-d `{
        "key":"MY_KEY"
    }`
```

> Response

```json
{ "data": [....], "next": "PAGINATION_URL" }
```

## Query Parameters

Name | Required | Type | Default | Description
---- | -------- | ---- | ------- | -----------
key | yes | string | | The API key

# Show a Blueprint information

```shell
curl --request GET https://api.alexandria.io/v1/blueprint/ID \
-H `Content-Type: application/json` \
-d `{
        "key":"MY_KEY"
    }`
```

> Response

```json
{
  "id": "BLUEPRINT ID",
  "name": "Blueprint name",
  "created_at": "ISO8601 date",
  "updated_at": "ISO8601 date",
  "fields": [{
    .... // the blueprint fields
  }],
  "items_count": 0
}
```

## Query Parameters

Name | Required | Type | Default | Description
---- | -------- | ---- | ------- | -----------
key | yes | string | | The API key

# Create an Item

## HTTP Request

```shell
curl https://api.alexandria.io/v1/item \
-H `Content-Type: application/json` \
-d `{
        "key": "MY_KEY",
        "blueprint_id": "BLUEPRINT ID",
        "data": [{
          "name": "foo",
          "price": 95.50
        }]
    }`
```

> Response (HTTP Status 200)

```json
{
  "id": "ITEM ID"
}
```

## Query Parameters

Name | Required | Type | Default | Description
---- | -------- | ---- | ------- | -----------
key | yes | string | | The API key
blueprint_id | yes | string | | The blueprint ID
data | yes | array | | An array containing the data according to the blueprint specification

# Update an Item

```shell
curl --request PUT https://api.alexandria.io/v1/item/ID \
-H `Content-Type: application/json` \
-d `{
        "key": "MY_KEY",
        "data": [{
          name: "bar"
        }]
    }`
```

> Response (HTTP Status 200)

```json
"OK"
```

## Query Parameters

Same as creating a item, except for the Blueprint ID.

# Delete an Item

```shell
curl --request DELETE https://api.alexandria.io/v1/item/ID \
-H `Content-Type: application/json` \
-d `{
        "key":"MY_KEY"
    }`
```

> Response

```json
"OK"
```

## Query Parameters

Name | Required | Type | Default | Description
---- | -------- | ---- | ------- | -----------
key | yes | string | | The API key

# List Items

```shell
curl --request GET https://api.alexandria.io/v1/items \
-H `Content-Type: application/json` \
-d `{
        "key":"MY_KEY",
        "blueprint_id": "BLUEPRINT ID"
    }`
```

> Response

```json
{ "data": [....], "next": "PAGINATION_URL" }
```

## Query Parameters

Name | Required | Type | Default | Description
---- | -------- | ---- | ------- | -----------
key | yes | string | | The API key
blueprint_id | yes | string | | The blueprint ID

# Show an Item Information

```shell
curl --request GET https://api.alexandria.io/v1/item/ID \
-H `Content-Type: application/json` \
-d `{
        "key":"MY_KEY"
    }`
```

> Response

```json
{
  "id": "ITEM ID",
  "blueprint_id": "Blueprint ID",
  "created_at": "ISO8601 date",
  "updated_at": "ISO8601 date",
  "data": [{
    .... // the blueprint fields
  }]
}
```

Name | Required | Type | Default | Description
---- | -------- | ---- | ------- | -----------
key | yes | string | | The API key
