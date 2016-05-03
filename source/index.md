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

Welcome to the Candidio API documentation.

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
production | ID | Scope assets by production ID.
stock | boolean | Scope assets that belong to My Brand, or inverse.
user | ID | Scope assets by user that created them.
workspace | ID | Scope assets by workspace they belong to.

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

Delete asset, scoped by workspace.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/assets/<ID>`

Delete asset, scoped by workspace and production.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets/<ID>`

## Briefs

### Get All Briefs

```http
GET /v1/workspaces/<ID>/productions/<ID>/briefs?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": [{
    "type": "brief",
		"id": "brf_hashhere",
		"purpose": "purpose description",
		"purpose_because": "purpose because desription",
		"description": null,
		"end_screen": null,
		"instructions": null,
		"meta": {
			"length": "3.0",
			"tone": {
				"action": false,
				"brief": false,
				"clean": false,
				"clever": false,
				"cool": false,
				"emotional": false,
				"fancy": false,
				"fast": false,
				"fresh": false,
				"fun": false,
				"funny": false,
				"happy": false,
				"inspiring": false,
				"inviting": false,
				"long": false,
				"mysterious": false,
				"powerful": false,
				"serious": false,
				"slow": false,
				"thoughtProvoking": false
			},
			"music": false,
			"musicType": null,
			"musicProvider": null,
			"videoType": "Other"
		},
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
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

This endpoint returns a collection of paginated briefs.

#### HTTP Request

Briefs route to get paginated collection scoped by workspace and production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
production | Production the brief belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
user | ID | Scope assets by user that created them.
workspace | ID | Scope assets by workspace they belong to.

### Get Specific Brief

```http
GET /v1/workspaces/<ID>/productions/<ID>/briefs/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "brief",
		"id": "brf_hashhere",
		"purpose": "purpose description",
		"purpose_because": "purpose because desription",
		"description": null,
		"end_screen": null,
		"instructions": null,
		"meta": {
			"length": "3.0",
			"tone": {
				"action": false,
				"brief": false,
				"clean": false,
				"clever": false,
				"cool": false,
				"emotional": false,
				"fancy": false,
				"fast": false,
				"fresh": false,
				"fun": false,
				"funny": false,
				"happy": false,
				"inspiring": false,
				"inviting": false,
				"long": false,
				"mysterious": false,
				"powerful": false,
				"serious": false,
				"slow": false,
				"thoughtProvoking": false
			},
			"music": false,
			"musicType": null,
			"musicProvider": null,
			"videoType": "Other"
		},
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
	},
}
```

This endpoint returns a collection of paginated briefs.

#### HTTP Request

Retrieve a specific brief scoped by workspace and production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
production | Production the brief belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
user | ID | Scope assets by user that created them.
workspace | ID | Scope assets by workspace they belong to.

### Create Brief

```http
POST /v1/workspaces/<ID>/productions/<ID>/briefs HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "brief",
		"id": "brf_hashhere",
		"purpose": "purpose description",
		"purpose_because": "purpose because description",
		"description": null,
		"end_screen": null,
		"instructions": null,
		"meta": {
			"length": "3.0",
			"tone": {
				"action": false,
				"brief": false,
				"clean": false,
				"clever": false,
				"cool": false,
				"emotional": false,
				"fancy": false,
				"fast": false,
				"fresh": false,
				"fun": false,
				"funny": false,
				"happy": false,
				"inspiring": false,
				"inviting": false,
				"long": false,
				"mysterious": false,
				"powerful": false,
				"serious": false,
				"slow": false,
				"thoughtProvoking": false
			},
			"music": false,
			"musicType": null,
			"musicProvider": null,
			"videoType": "Other"
		},
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
	},
}
```

Create a brief.

#### HTTP Request

Create a brief for a specific workspace and production.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
purpose | no | "People who watch this video will..."
purpose_because | no | "because I show and tell them..."
description | no | Brief description.
end_screen | no | End screen instructions.
instructions | no | Additional instructions.
meta | no | Array of brief meta data.
meta.length | no | Desired running time of final production.
meta.tone | no | Array of tone options.
meta.tone.action | no | ...
meta.tone.brief | no | ...
meta.tone.clean | no | ...
meta.tone.clever | no | ...
meta.tone.cool | no | ...
meta.tone.emotional | no | ...
meta.tone.fancy | no | ...
meta.tone.fast | no | ...
meta.tone.fresh | no | ...
meta.tone.fun | no | ...
meta.tone.funny | no | ...
meta.tone.happy | no | ...
meta.tone.inspiring | no | ...
meta.tone.inviting | no | ...
meta.tone.long | no | ...
meta.tone.mysterious | no | ...
meta.tone.powerful | no | ...
meta.tone.serious | no | ...
meta.tone.slow | no | ...
meta.tone.thoughtProvoking | no | ...
meta.videoType | no | ...
meta.musicProvider | no | ...
meta.musicType | no | ...
meta.music | no | ...

### Update Brief

```http
PUT /v1/workspaces/<ID>/productions/<ID>/briefs/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "brief",
		"id": "brf_hashhere",
		"purpose": "purpose description updated",
		"purpose_because": "purpose because description",
		"description": null,
		"end_screen": null,
		"instructions": null,
		"meta": {
			"length": "3.0",
			"tone": {
				"action": false,
				"brief": false,
				"clean": false,
				"clever": false,
				"cool": false,
				"emotional": false,
				"fancy": false,
				"fast": false,
				"fresh": false,
				"fun": false,
				"funny": false,
				"happy": false,
				"inspiring": false,
				"inviting": false,
				"long": false,
				"mysterious": false,
				"powerful": false,
				"serious": false,
				"slow": false,
				"thoughtProvoking": false
			},
			"music": false,
			"musicType": null,
			"musicProvider": null,
			"videoType": "Other"
		},
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
	},
}
```

Update a brief.

#### HTTP Request

Update a brief for a specific workspace and production.

`PUT https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
purpose | no | "People who watch this video will..."
purpose_because | no | "because I show and tell them..."
description | no | Brief description.
end_screen | no | End screen instructions.
instructions | no | Additional instructions.
meta | no | Array of brief meta data.
meta.length | no | Desired running time of final production.
meta.tone | no | Array of tone options.
meta.tone.action | no | ...
meta.tone.brief | no | ...
meta.tone.clean | no | ...
meta.tone.clever | no | ...
meta.tone.cool | no | ...
meta.tone.emotional | no | ...
meta.tone.fancy | no | ...
meta.tone.fast | no | ...
meta.tone.fresh | no | ...
meta.tone.fun | no | ...
meta.tone.funny | no | ...
meta.tone.happy | no | ...
meta.tone.inspiring | no | ...
meta.tone.inviting | no | ...
meta.tone.long | no | ...
meta.tone.mysterious | no | ...
meta.tone.powerful | no | ...
meta.tone.serious | no | ...
meta.tone.slow | no | ...
meta.tone.thoughtProvoking | no | ...
meta.videoType | no | ...
meta.musicProvider | no | ...
meta.musicType | no | ...
meta.music | no | ...

### Delete Brief

```http
DELETE /v1/workspaces/<ID>/productions/<ID>/briefs/<ID> HTTP/1.1
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

Delete a brief.

#### HTTP Request

Delete a brief, scoped by workspace and production.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs/<ID>`

## Productions

### Get All Productions

```http
GET /v1/workspaces/<ID>/productions?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": [{
    "type": "production",
		"id": "prd_hashhere",
		"title": "Title of Production",
    "status_state": "Planning",
    "status_queued": false,
    "allow_public_upload": false,
    "allow_public_shotlist": false,
    "goal_date": "2016-04-16 00:00:00",
    "first_submitted_at": null,
    "last_submitted_at": null,
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
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

This endpoint returns a collection of paginated productions.

#### HTTP Request

Productions route with no scopes, good for admin operations.

`GET https://api.candidio.com/v1/productions`

Productions route to get paginated collection scoped by workspace.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions`

Productions route to get paginated collection scoped by workspace and user.

`GET https://api.candidio.com/v1/workspaces/<ID>/users/<ID>/productions`

Productions route to get paginated collection scoped by workspace and project.

`GET https://api.candidio.com/v1/workspaces/<ID>/projects/<ID>/productions`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
brief | Latest brief created for a production.
owner | Person who created a production.
project | Project production belongs to, if any.
template | Template production was created from, if any.
workspace | Workspace a production belongs to.
assets | Assets attached to a production.
briefs | All briefs attached to a production.
descriptions | Shot descriptions attached to a production.
sharing_users | Users a production has been shared with.
snapshots | Production snapshots captured between status changes.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
allowsPublicUpload | boolean | Scope by whether a production allows public upload.
asset | ID | Scope productions by asset.
project | ID | Scope productions by project.
projectNull | boolean | Scope by project null or not null.
projectUser | ID | Scope productions by user with permission to see parent project.
user | ID | Scope productions by user that created them.
workspace | ID | Scope productions by workspace they belong to.

### Get Specific Production

```http
GET /v1/workspaces/<ID>/productions/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "production",
		"id": "prd_hashhere",
		"title": "Title of Production",
    "status_state": "Planning",
    "status_queued": false,
    "allow_public_upload": false,
    "allow_public_shotlist": false,
    "goal_date": "2016-04-16 00:00:00",
    "first_submitted_at": null,
    "last_submitted_at": null,
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
	},
}
```

This endpoint returns a collection of paginated productions.

#### HTTP Request

Route to get specific production with no scopes.

`GET https://api.candidio.com/v1/productions/<ID>`

Route to get specific production scoped by workspace.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>`

Route to get specific production scoped by workspace and user.

`GET https://api.candidio.com/v1/workspaces/<ID>/users/<ID>/productions/<ID>`

Route to get specific production scoped by workspace and project.

`GET https://api.candidio.com/v1/workspaces/<ID>/projects/<ID>/productions/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
brief | Latest brief created for a production.
owner | Person who created a production.
project | Project production belongs to, if any.
template | Template production was created from, if any.
workspace | Workspace a production belongs to.
assets | Assets attached to a production.
briefs | All briefs attached to a production.
descriptions | Shot descriptions attached to a production.
sharing_users | Users a production has been shared with.
snapshots | Production snapshots captured between status changes.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
allowsPublicUpload | boolean | Scope by whether a production allows public upload.
asset | ID | Scope productions by asset.
project | ID | Scope productions by project.
projectNull | boolean | Scope by project null or not null.
projectUser | ID | Scope productions by user with permission to see parent project.
user | ID | Scope productions by user that created them.
workspace | ID | Scope productions by workspace they belong to.

### Create Production

```http
POST /v1/workspaces/<ID>/productions HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "production",
		"id": "prd_hashhere",
		"title": "Title of Production",
    "status_state": "Planning",
    "status_queued": false,
    "allow_public_upload": false,
    "allow_public_shotlist": false,
    "goal_date": "2016-04-16 00:00:00",
    "first_submitted_at": null,
    "last_submitted_at": null,
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
	},
}
```

Create a production.

#### HTTP Request

Route to create production.

`POST https://api.candidio.com/v1/productions`

Route to create a production for a specific workspace.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions`

Route to create a production for a specific workspace and project.

`POST https://api.candidio.com/v1/workspaces/<ID>/projects/<ID>/productions`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
allow_public_upload | sometimes | Boolean, allows public uploads.
allow_public_shotlist | sometimes | Boolean, allows public shotlist.
goal_date | sometimes | Production goal date in `Y-m-d H:i:s` format.
production_id | sometimes | Production to clone from.
project_id | sometimes | Project to attach production to.
status | sometimes | Default "planning". Only administrators can create a production with a specific status.
template_id | sometimes | Template to create from.
title | yes* | Title for production, if not being created from template or cloned.


### Update Production

```http
PUT /v1/workspaces/<ID>/productions/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "production",
		"id": "prd_hashhere",
		"title": "Title of Production",
    "status_state": "Planning",
    "status_queued": false,
    "allow_public_upload": false,
    "allow_public_shotlist": false,
    "goal_date": "2016-04-16 00:00:00",
    "first_submitted_at": null,
    "last_submitted_at": null,
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
	},
}
```

Update a production.

#### HTTP Request

Route to update a production.

`PUT https://api.candidio.com/v1/productions/<ID>`

Route to update a production belonging to a specific workspace.

`PUT https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>`

Route to update a production belonging to a specific workspace and project.

`PUT https://api.candidio.com/v1/workspaces/<ID>/projects/<ID>/productions/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
allow_public_upload | sometimes | Boolean, allows public uploads.
allow_public_shotlist | sometimes | Boolean, allows public shotlist.
goal_date | sometimes | Production goal date in `Y-m-d H:i:s` format.
is_queued | sometimes | Boolean, queues production when true.
project_id | sometimes | Project to attach production to.
status | sometimes | Default "planning". Only administrators can create a production with a specific status.
title | yes* | Title for production, if not being created from template or cloned.


### Delete Production

```http
DELETE /v1/workspaces/<ID>/productions/<ID> HTTP/1.1
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

Delete a production.

#### HTTP Request

Route to delete a production.

`DELETE https://api.candidio.com/v1/productions/<ID>`

Route to delete a production belonging to a specific workspace.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>`

Route to delete a production belonging to a specific workspace and project.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/projects/<ID>/productions/<ID>`

## Projects

### Get All Projects

```http
GET /v1/projects?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": [{
    "type": "project",
		"id": "prj_hashhere",
		"name": "Project Name",
		"internal_notes": "Internal notes about this project.",
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

These endpoints return a collection of paginated projects.

#### HTTP Request

Get projects.

`GET https://api.candidio.com/v1/projects`

Get projects scoped by workspace.

`GET https://api.candidio.com/v1/workspaces/<ID>/projects`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
owner | User that created a project.
productions | Productions in a project.
sharing_users | Users a project has been shared with.
workspace | Workspace a project belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
user | ID | Scope projects by creator or sharing users.
workspace | ID | Scope projects by workspace they belong to.

### Get a Specific Project

```http
GET /v1/projects/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "project",
		"id": "prj_hashhere",
		"name": "Project Name",
		"internal_notes": "Internal notes about this project.",
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints return a specific project.

#### HTTP Request

Get project.

`GET https://api.candidio.com/v1/projects/<ID>`

Get project scoped by workspace.

`GET https://api.candidio.com/v1/workspaces/<ID>/projects/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
owner | User that created a project.
productions | Productions in a project.
sharing_users | Users a project has been shared with.
workspace | Workspace a project belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
user | ID | Scope project by creator or sharing users.
workspace | ID | Scope project by workspace it belongs to.

### Create Project

```http
POST /v1/workspaces/<ID>/projects HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"name": "Project Name"
    }
  }
}
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "project",
    "id": "prj_hashhere",
    "name": "Project Name",
    "internal_notes": "Internal notes about this project.",
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints create projects.

#### HTTP Request

Create project.

`POST https://api.candidio.com/v1/projects`

Create project that belongs to a workspace.

`POST https://api.candidio.com/v1/workspaces/<ID>/projects`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
workspace_id | yes* | Defines workspace to assign shot to.
name | yes | Project name.
internal_notes | no | Internal notes, for administrators only.

### Update Project

```http
POST /v1/workspaces/<ID>/projects/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"name": "Project Name Updated"
    }
  }
}
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "project",
    "id": "prj_hashhere",
    "name": "Project Name Updated",
    "internal_notes": "Internal notes about this project.",
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints update projects.

#### HTTP Request

Update project.

`POST https://api.candidio.com/v1/projects/<ID>`

Update project scoped by workspace.

`POST https://api.candidio.com/v1/workspaces/<ID>/projects/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
workspace_id | yes* | Defines workspace to scope shot by.
name | yes | Project name.
internal_notes | no | Internal notes, for administrators only.

### Delete Project

```http
DELETE /v1/workspaces/<ID>/projects/<ID> HTTP/1.1
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

These endpoints delete a specific project.

#### HTTP Request

Delete a project.

`DELETE https://api.candidio.com/v1/projects/<ID>`

Delete a project scoped by workspace.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/projects/<ID>`

## Shots

### Get All Shots

```http
GET /v1/workspaces/<ID>/descriptions?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": [{
    "type": "description",
		"id": "dsc_hashhere",
		"position": 0,
		"shot_type": "broll",
		"fields": {
			"field1": "This shot's description.",
			"field2": "",
			"meta": []
		}
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

These endpoints return a collection of paginated shots.

#### HTTP Request

Get shots scoped by workspace.

`GET https://api.candidio.com/v1/workspaces/<ID>/descriptions`

Get shots scoped by workspace and production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/descriptions`

Get shots for a public production while it remains in planning state. Authorization token is not required.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/descriptions/public`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
assets | Collection of assets that belong to this shot description.
production | Production the shot belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
asset | ID | Scopes shots by asset ID.
production | ID | Scope shots by production they belong to.
workspace | ID | Scope shots by workspace they belong to.

### Get a Specific Shot

```http
GET /v1/workspaces/<ID>/descriptions/dsc_hashhere HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "description",
		"id": "dsc_hashhere",
		"position": 0,
		"shot_type": "broll",
		"fields": {
			"field1": "This shot's description.",
			"field2": "",
			"meta": []
		}
	}
}
```

These endpoints return a specific shot.

#### HTTP Request

Get shot scoped by workspace.

`GET https://api.candidio.com/v1/workspaces/<ID>/descriptions/<ID>`

Get shot scoped by workspace and production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/descriptions/<ID>`

#### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
workspace_id | no | For permissions, if action isn't performed by an admin and isn't set in URL.

### Create Shot

```http
POST /v1/workspaces/<ID>/productions/<ID>/descriptions HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "type": "broll",
    "fields": {
      "field1": "Shot description.",
      "field2": "",
      "meta": []
    }
  }
}
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "description",
		"id": "dsc_hashhere",
		"position": 0,
		"shot_type": "broll",
		"fields": {
			"field1": "This shot's description.",
			"field2": "",
			"meta": []
		}
	}
}
```

These endpoints create shots.

#### HTTP Request

Create shot that belongs to the workspace?? (this may be unecessary)

`POST https://api.candidio.com/v1/workspaces/<ID>/descriptions`

Create shot that belongs to a production.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/descriptions`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
production_id | yes* | Defines production to assign shot to.
type | yes | Shot type. This may be depreciated.
fields | yes | Array blob of field options.
fields.field1 | sometimes | String, purpose depends.
fields.field2 | sometimes | String, purpose depends.
fields.meta | sometimes | String, purpose depends.
fields.meta.name | sometimes | String for lower third name.
fields.meta.title | sometimes | String for lower third title.

### Update Shot

```http
PUT /v1/workspaces/<ID>/productions/<ID>/descriptions/dsc_hashhere HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "position": 3,
    "type": "broll",
    "fields": {
      "field1": "Shot description with more text.",
      "field2": "",
      "meta": []
    }
  }
}
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "description",
		"id": "dsc_hashhere",
		"position": 3,
		"shot_type": "broll",
		"fields": {
			"field1": "Shot description with more text.",
			"field2": "",
			"meta": []
		}
	}
}
```

These endpoints create shots.

#### HTTP Request

Update shot that belongs to the workspace?? (this may be unecessary)

`PUT https://api.candidio.com/v1/workspaces/<ID>/descriptions/<ID>`

Update shot that belongs to a production.

`PUT https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/descriptions/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
position | no | Moves the shot's position within shotlist.
type | yes | Shot type. This may be depreciated.
fields | yes | Array blob of field options.
fields.field1 | sometimes | String, purpose depends.
fields.field2 | sometimes | String, purpose depends.
fields.meta | sometimes | String, purpose depends.
fields.meta.name | sometimes | String for lower third name.
fields.meta.title | sometimes | String for lower third title.

### Delete Shot

```http
DELETE /v1/workspaces/<ID>/productions/<ID>/descriptions/dsc_hashhere HTTP/1.1
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

These endpoints delete a specific shot.

#### HTTP Request

Delete a shot scoped by workspace.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/descriptions/<ID>`

Delete a shot scoped by workspace and production.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/descriptions/<ID>`

### Attach Shot to Asset

```http
PUT /v1/workspaces/<ID>/assets/<ID>/descriptions/<ID>/attach HTTP/1.1
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

Attach shot description to asset.

#### HTTP Request

Attach shot description to asset, scoped by workspace.

`PUT https://api.candidio.com/v1/workspaces/<ID>/assets/<ID>/descriptions/<ID>/attach`

### Detach Shot from Asset

```http
DELETE /v1/workspaces/<ID>/assets/<ID>/descriptions/<ID>/detach HTTP/1.1
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

Detach shot description from asset.

#### HTTP Request

Detach shot description from asset, scoped by workspace.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/assets/<ID>/descriptions/<ID>/detach`

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
