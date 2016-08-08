## Assets

### List Assets

```http
GET /v1/assets?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



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
created_by | User who uploaded the asset.
uploadable | Uploadable relation.
workspace | Workspace the asset belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
assetType | audio,image,video,other | Scopes assets by mimetype with fallback on file extension.
completed | boolean | Scope assets that are completed productions, or inverse.
descriptionType | string | Scope assets why attached shot description type.
hasFailedJobs | boolean | Scope assets that are missing thumbnails or haven't had previews generated.
description | ID | Scope assets by description. ID optional.
deliverable | ID | Scope assets by deliverable. ID optional.
production | ID | Scope assets by production. ID optional.
revision | ID | Scope assets by revision. ID optional.
videoSeries | ID | Scope assets by video_series. ID optional.
user | ID | Scope assets by user that created them.
workspace | ID | Scope assets by workspace they belong to.

### Get a Specific Asset

```http
GET /v1/assets/ast_hashhere HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



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

#### Embeddable Relationships

Relationship | Description
------------ | -----------
created_by | User who uploaded the asset.
uploadable | Uploadable relation.
workspace | Workspace the asset belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
assetType | audio,image,video,other | Scopes assets by mimetype with fallback on file extension.
completed | boolean | Scope assets that are completed productions, or inverse.
descriptionType | string | Scope assets why attached shot description type.
hasFailedJobs | boolean | Scope assets that are missing thumbnails or haven't had previews generated.
description | ID | Scope assets by description. ID optional.
deliverable | ID | Scope assets by deliverable. ID optional.
production | ID | Scope assets by production. ID optional.
revision | ID | Scope assets by revision. ID optional.
videoSeries | ID | Scope assets by video_series. ID optional.
user | ID | Scope assets by user that created them.
workspace | ID | Scope assets by workspace they belong to.

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

To create an asset for a specific Workspace without assigning an Uploadable relation.

`POST https://api.candidio.com/v1/workspaces/<ID>/assets`

To create an asset for a specific Production.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/assets`

Assets can also be created for public Productions.

`POST https://api.candidio.com/v1/public/workspaces/<ID>/productions/<ID>/assets`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | ------- | -----------
data.workspace_id | yes\* | Assign new asset to this workspace.
data.deliverable_id | sometimes\*\* | Attach to Deliverable.
data.description_id | sometimes\*\* | Attach to Description.
data.production_id | sometimes\*\* | Attach to Production.
data.revision_id | sometimes\*\* | Attach to Revision.
data.video_series_id | sometimes\*\* | Attach to Video-Series.
data.bucket | yes | S3 bucket where file is located.
data.object_key | yes | S3 object key of file.
data.file_name | yes | Original filename.
data.file_type | yes | File extension.
data.size | yes | Size of file in bytes.
data.mimetype | yes | File mimetype.
data.is_completed_production | no | Default `false`, set `true` for completed productions.

<aside class="success">
* Workspace only required when creating on core assets route.
** Only one Uploadable relationship ID may be used at a time.
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
data.deliverable_id | sometimes\* | Attach to Deliverable.
data.description_id | sometimes\* | Attach to Description.
data.production_id | sometimes\* | Attach to Production.
data.revision_id | sometimes\* | Attach to Revision.
data.video_series_id | sometimes\* | Attach to Video-Series.
data.bucket | yes | S3 bucket where file is located.
data.object_key | yes | S3 object key of file.
data.file_name | yes | Original filename.
data.file_type | yes | File extension.
data.size | yes | Size of file in bytes.
data.mimetype | yes | File mimetype.
data.is_completed_production | no | Default `false`, set `true` for completed productions.

<aside class="success">
* Only one Uploadable relationship ID may be used at a time.
</aside>

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
