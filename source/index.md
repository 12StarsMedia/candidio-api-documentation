---
title: Candidio API Reference

language_tabs:
  - http

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

You can embed related models and collections. Check documentation for specific relationships available on each resource. Dot notation can be used to retrieve further levels of nesting (i.e. ?inclue=workspace.users).

#### Query Parameters

Parameter | Description
--------- | -----------
include | Embed a related resource.

## Pagination

Most resources will return a paginated collection of results.

#### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
limit | 100 | Limit records returned in pagination.
page | 1 | Offset to request from pagination.

## Scoping

Most resources can be scoped by workspace and user. See list of available scopes for each resource type.

#### Query Parameters

Parameter | Description
--------- | -----------
scope | Scope by user, workspace, etc.

## Sorting

#### Query Parameters

Parameter | Description
--------- | -----------
sort | Field to order records by.
direction | Direction of sorting, `asc` or `desc`.

# Core Resources

## Assets

### Get All Assets

```http
GET /v1/assets?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": [{
			"type": "asset",
			"id": "ast_hashhere",
			"file_name": "file",
			"file_type": "mp4",
			"mimetype": "video\/mp4",
			"size": 1234567890,
			"video_duration": null,
			"is_stock": false,
			"is_transcoded": false,
			"is_completed_production": false,
			"link_download": "https:\/\/s3.amazonaws.com\/upload.candidio.com\/path\/to\/file.mp4",
			"link_thumbnail": null,
			"link_fullsize": null,
			"link_preview_mp4": null,
			"link_preview_webm": null,
			"created_at": "2016-04-04 07:28:30",
			"updated_at": "2016-04-04 07:28:30"
	}],
  "meta": {
		"pagination": {
			"total": 4,
			"count": 4,
			"per_page": 100,
			"current_page": 1,
			"total_pages": 1,
			"links": []
		}
	}
}
```

These endpoints return a collection of paginated assets.

#### HTTP Request

Simple assets route, useful for admin level actions needing little scope.

`GET https://api.candidio.com/v1/assets`

To create an asset for a specific Workspace (Good for My Brand).

`GET https://api.candidio.com/v1/workspaces/<ID>/assets`

To create an asset for a specific Production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets`

#### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
include | no | Embed a related resource.
limit | no | Limit records returned in pagination.
page | no | Offset to request from pagination.
scope | no | Scope by user, workspace, etc.
sort | no | Field to order records by.
direction | no | Direction of sorting, `asc` or `desc`.
workspace_id | no | For permissions, if action isn't performed by an admin and isn't set in URL.

#### Embeddable Relationships

Relationship | Description
------------ | -----------
description | Shot description the asset is attached to, if any.
owner | User who uploaded the asset.
production | Production the asset is attached to, if any.
workspace | Workspace the asset belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
assetType | audio,image,video,other | Scopes assets by mimetype with fallback on file extension.
completed | boolean | Scope assets that are completed productions, or inverse.
descriptionType | string | Scope assets why attached shot description type.
hasFailedJobs | boolean | Scope assets that are missing thumbnails or haven't had previews generated.
production | <ID> | Scope assets by production ID.
stock | boolean | Scope assets that belong to My Brand, or inverse.
user | <ID> | Scope assets by user that created them.
workspace | <ID> | Scope assets by workspace they belong to.

### Get a Specific Asset

```http
GET /v1/assets/ast_hashhere HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
			"type": "asset",
			"id": "ast_hashhere",
			"file_name": "file",
			"file_type": "mp4",
			"mimetype": "video\/mp4",
			"size": 1234567890,
			"video_duration": null,
			"is_stock": false,
			"is_transcoded": false,
			"is_completed_production": false,
			"link_download": "https:\/\/s3.amazonaws.com\/upload.candidio.com\/path\/to\/file.mp4",
			"link_thumbnail": null,
			"link_fullsize": null,
			"link_preview_mp4": null,
			"link_preview_webm": null,
			"created_at": "2016-04-04 07:28:30",
			"updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints return a specific asset.

#### HTTP Request

Simple assets route, useful for admin level actions needing little scope.

`GET https://api.candidio.com/v1/assets/<ID>`

To retrieve an asset for a specific workspace (Good for My Brand).

`GET https://api.candidio.com/v1/workspaces/<ID>/assets/<ID>`

To retrieve an asset for a specific production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets/<ID>`

#### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | no | Embed a related resource.
scope | no | Scope by user, workspace, etc.
workspace_id | no | For permissions, if action isn't performed by an admin and isn't set in URL.

### Create Asset

```http
POST /v1/assets/ HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
    "data": {
        "workspace_id": "wrk_hashhere",
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
{
	"data": {
		"type": "asset",
		"id": "ast_hashhere",
		"file_name": "meowcats",
		"file_type": "mp4",
		"mimetype": "video\/mp4",
		"size": 1234567890,
		"video_duration": null,
		"is_stock": false,
		"is_transcoded": false,
		"is_completed_production": false,
		"link_download": "https:\/\/s3.amazonaws.com\/upload.candidio.com\/path\/to\/file.mp4?someargs",
		"link_thumbnail": null,
		"link_fullsize": null,
		"link_preview_mp4": null,
		"link_preview_webm": null,
		"created_at": "2016-04-04 07:28:30",
		"updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints create assets.

#### HTTP Request

Simple assets route, useful for admin level actions needing little scope.

`POST https://api.candidio.com/v1/assets`

To create an asset for a specific Workspace (Good for My Brand).

`POST https://api.candidio.com/v1/workspaces/<ID>/assets`

To create an asset for a specific Production.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets`

Assets can also be created for public Productions.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets/public`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | ------- | -----------
data.workspace_id | yes\* | Assign new asset to this workspace.
data.user_id | yes | Assign new asset to this user.
data.production_id | sometimes\* | Assign new asset to this production.
data.description_id | no | Assign this description to new asset.
data.bucket | yes | S3 bucket where file is located.
data.object_key | yes | S3 object key of file.
data.file_name | yes | Original filename.
data.file_type | yes | File extension.
data.size | yes | Size of file in bytes.
data.mimetype | yes | File mimetype.
data.is_completed_production | no | Default `false`, set `true` for completed productions.
data.is_stock | no | Set `true` when creating asset for My Brand.

<aside class="success">
* Required IDs are not required when they are already present in the URL.
</aside>

### Update Asset

```http
PUT /v1/assets/ast_hashhere HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
    "data": {
        "workspace_id": "wrk_hashhere",
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
{
	"data": {
		"type": "asset",
		"id": "ast_hashhere",
		"file_name": "meowcats",
		"file_type": "mp4",
		"mimetype": "video\/mp4",
		"size": 1234567890,
		"video_duration": null,
		"is_stock": false,
		"is_transcoded": false,
		"is_completed_production": false,
		"link_download": "https:\/\/s3.amazonaws.com\/upload.candidio.com\/path\/to\/file.mp4?someargs",
		"link_thumbnail": null,
		"link_fullsize": null,
		"link_preview_mp4": null,
		"link_preview_webm": null,
		"created_at": "2016-04-04 07:28:30",
		"updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints update a specific asset.

#### HTTP Request

Simple assets route, useful for admin level actions needing little scope.

`PUT https://api.candidio.com/v1/assets/<ID>`

Update an asset while scoping within a specific workspace.

`PUT https://api.candidio.com/v1/workspaces/<ID>/assets/<ID>`

Update an asset while scoping within a specific production.

`PUT https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | ------- | -----------
data.workspace_id | no | Assign new asset to this workspace.
data.user_id | no | Assign new asset to this user.
data.production_id | no | Assign new asset to this production.
data.file_name | no | Original filename and display name.
data.is_stock | no | True is asset belongs to My Brand.
data.is_transcoded | no | True if asset has been transcoded.

<aside class="success">
Assets should not need to be updated, these routes mostly exist in case there were ever a need to correct mistakes.
</aside>

### Delete Asset

```http
DELETE /v1/assets/ast_hashhere HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"success": {
		"http_code": 200,
		"message": "Success"
	}
}
```

These endpoints delete a specific asset.

#### HTTP Request

Simple assets route, useful for admin level actions needing little scope.

`DELETE https://api.candidio.com/v1/assets/<ID>`

To retrieve an asset for a specific workspace (Good for My Brand).

`DELETE https://api.candidio.com/v1/workspaces/<ID>/assets/<ID>`

To retrieve an asset for a specific production.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets/<ID>`

#### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
include | no | Embed a related resource.
scope | no | Scope by user, workspace, etc.
workspace_id | no | For permissions, if action isn't performed by an admin and isn't set in URL.

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
