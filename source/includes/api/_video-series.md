## Video-Series

### List Video-Series

```http
GET /v1/video-series?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": [{
    "type": "video-series",
		"id": "vds_hashhere",
		"title": "VideoSeries title",
		"audience": "",
		"synopsis": "",
		"turnaround": 5,
		"video_length": "120.0",
		"internal_notes": "Internal notes about this video-series.",
		"is_published": false,
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

These endpoints return a collection of paginated video-series.

#### HTTP Request

Get video-series.

`GET https://api.candidio.com/v1/video-series`

Get video-series scoped by workspace.

`GET https://api.candidio.com/v1/workspaces/<ID>/video-series`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
created_by | User that created a video-series.
example_video | Asset containing an example of what videos in this series will look like.
template | Template to be used for Productions in this video-series.
workspace | Workspace a video-series belongs to.
assets | Brand assets belonging to this video-series.
productions | Productions in a video-series.
collaborators | Users a video-series has been shared with.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
published | boolean | Scope by published or unpublished Video-Series.
user | ID | Scope video-series by creator or sharing users.
workspace | ID | Scope video-series by workspace they belong to.

### Get a Specific Video-Series

```http
GET /v1/video-series/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": {
    "type": "video-series",
		"id": "vds_hashhere",
		"title": "VideoSeries Name",
		"audience": "",
		"synopsis": "",
		"turnaround": 5,
		"video_length": "120.0",
		"internal_notes": "Internal notes about this video-series.",
		"is_published": false,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints return a specific video-series.

#### HTTP Request

Get video-series.

`GET https://api.candidio.com/v1/video-series/<ID>`

Get video-series scoped by workspace.

`GET https://api.candidio.com/v1/workspaces/<ID>/video-series/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
created_by | User that created a video-series.
example_video | Asset containing an example of what videos in this series will look like.
template | Template to be used for Productions in this video-series.
workspace | Workspace a video-series belongs to.
assets | Brand assets belonging to this video-series.
productions | Productions in a video-series.
collaborators | Users a video-series has been shared with.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
published | boolean | Scope by published or unpublished Video-Series.
user | ID | Scope video-series by creator or sharing users.
workspace | ID | Scope video-series by workspace it belongs to.

### Create VideoSeries

```http
POST /v1/workspaces/<ID>/video-series HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"title": "VideoSeries Name",
			"example_video_id": "ast_hashhere",
			"video_length": "120.0"
  }
}
```

```json
{
	"data": {
    "type": "video-series",
    "id": "vds_hashhere",
    "title": "VideoSeries Name",
		"audience": "",
		"synopsis": "",
		"turnaround": 5,
		"video_length": "120.0",
		"internal_notes": "Internal notes about this video-series.",
		"is_published": false,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30",
		"example_video": {
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
}
```

These endpoints create video-series.

#### HTTP Request

Create video-series.

`POST https://api.candidio.com/v1/video-series`

Create video-series that belongs to a workspace.

`POST https://api.candidio.com/v1/workspaces/<ID>/video-series`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
workspace_id | yes* | Defines workspace to assign shot to.
template_id | no | Template to use for Productions in this Video-Series.
example_video_id | no | Asset to use as example for this Video-Series.
title | yes | Video-Series title.
audience | no | Intended audience for this Video-Series.
synopsis | no | Description of this Video-Series.
turnaround | no | Number of days to turnaround a Production. Default 5.
video_length | no | Desired duration of videos in series.
internal_notes | no | Internal notes, for administrators only.
is_published | no | Visibility to Producers. Default is `false`.

### Update VideoSeries

```http
PUT /v1/workspaces/<ID>/video-series/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"title": "VideoSeries Name Updated",
			"example_video_id": "ast_hashhere"
  }
}
```

```json
{
	"data": {
    "type": "video-series",
    "id": "vds_hashhere",
    "title": "VideoSeries Name Updated",
		"audience": "",
		"synopsis": "",
		"turnaround": 5,
		"video_length": "120.0",
    "internal_notes": "Internal notes about this video-series.",
		"is_published": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30",
		"example_video": {
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
}
```

These endpoints update video-series.

#### HTTP Request

Update video-series.

`PUT https://api.candidio.com/v1/video-series/<ID>`

Update video-series scoped by workspace.

`PUT https://api.candidio.com/v1/workspaces/<ID>/video-series/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
template_id | no | Template to use for Productions in this Video-Series.
example_video_id | no | Asset to use as example for this Video-Series.
title | yes | Video-Series title.
audience | no | Intended audience for this Video-Series.
synopsis | no | Description of this Video-Series.
turnaround | no | Number of days to turnaround a Production. Default 5.
video_length | no | Desired duration of videos in series.
internal_notes | no | Internal notes, for administrators only.
is_published | no | Visibility to Producers. Default is `false`.

### Delete VideoSeries

```http
DELETE /v1/workspaces/<ID>/video-series/<ID> HTTP/1.1
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

These endpoints delete a specific video-series.

#### HTTP Request

Delete a video-series.

`DELETE https://api.candidio.com/v1/video-series/<ID>`

Delete a video-series scoped by workspace.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/video-series/<ID>`
