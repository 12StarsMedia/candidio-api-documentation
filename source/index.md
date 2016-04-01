---
title: Candidio API Reference

language_tabs:
  - shell
  - php

toc_footers:
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

## Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](http://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Topics

## Authentication
## Nesting Models
## Pagination
## Versioning

# Core Resources

## Assets

### Get All Assets

Get all assets.

### Create Asset

```http
POST /v1/assets/ HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
    "data": {
        "workspace_id": "wrk_krVZWGaJ",
        "bucket": "upload.candidio.com",
        "object_key": "path/to/file.mp4",
        "file_name": "file.mp4",
        "file_type": "mp4",
        "size": 1234567890,
        "mimetype": "image/mp4"
    }
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

These endpoints create asset records.

### HTTP Request

Simple assets route, useful for admin level actions needing little scope.

`POST https://api.candidio.com/v1/assets`

To create an asset for a specific Workspace (Good for My Brand).

`POST https://api.candidio.com/v1/workspaces/<ID>/assets`

To create an asset for a specific Production.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets`

Assets can also be created for public Productions.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets/public`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
workspace_id | yes | Assign new asset to this workspace.
user_id | yes | Assign new asset to this user.
production_id | no | Assign new asset to this production.
description_id | no | Assign this description to new asset.
bucket | yes | S3 bucket where file is located.
object_key | yes | S3 object key of file.
file_name | yes | Original filename.
file_type | yes | File extension.
size | yes | Size of file in bytes.
mimetype | yes | File mimetype.
is_completed_production | no | Default `false`, set `true` for completed productions.
is_stock | no | Set `true` when creating asset for My Brand.

<aside class="success">
Required IDs are not required when they are already present in the URL.
</aside>

## Briefs
## Productions
## Projects
## Shots
## Workspaces

# Account

## Create Account

Create a new workspace with attached new user account.

This is a public route and authorization is not necessary.

```http
POST https://api.candidio.com/v1/register HTTP/1.1
Origin: https://api.candidio.com
Content-Type: application/json

{
"data": {
"first_name": "Test",
"last_name": "McTestface",
"email": "producer@candidio.com",
"password": "can-test",
"is_business": false,
"company": "McTestface Studios"
}
}
```
> All fields required unless `is_business` is set to `false`, in which case `company` becomes optional.


## Activate Account
## Cancel Account
## Update User Details
## Update Workspace Details

# Billing

## Add/Update Credit Card
## Credit Account
## Debit Account

# Plans

## Update Plan
## Cancel Plan
## Resume Plan
## Industries

# Roles & Permissions

# Templates

## Templates
## Template Collections
## Template Types
