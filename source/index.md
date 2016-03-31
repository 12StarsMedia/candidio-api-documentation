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

```
/v1/assets

```
> Assets can be scoped by Workspace or Workspace-Production.
> `/v1/workspaces/:workspace:/assets`
> `/v1/workspaces/:workspace:/productions/:production:/assets`

## Briefs
## Productions
## Projects
## Shotlists
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
