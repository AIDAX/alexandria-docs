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
fields | yes | array | | An array containing the blueprint fields(types available are string, boolean and number)

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

# Delete a Blueprint

```shell
curl --request DELETE https://api.alexandria.io/v1/hook/ID
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