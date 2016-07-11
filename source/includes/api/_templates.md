## Templates

### List Templates

```http
GET /v1/templates?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": [{
    "type": "template",
		"id": "tmp_hashhere",
		"name": "Template Name",
		"description": "Template description.",
    "is_published": true,
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

These endpoints return a collection of paginated templates.

#### HTTP Request

Route to list templates.

`GET https://api.candidio.com/v1/templates`

Public route to list templates.

`GET https://api.candidio.com/v1/public/templates`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
industry | Industry this Template belongs to.
workspace | Workspace this Template belongs to.
template_type | Template-Type this Template belongs to.

### Get a Specific Template

```http
GET /v1/templates/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": {
    "type": "template",
		"id": "tmp_hashhere",
		"name": "Template Name",
		"description": "Template description.",
    "is_published": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints return a specific template.

#### HTTP Request

Get template.

`GET https://api.candidio.com/v1/templates/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
industry | Industry this Template belongs to.
workspace | Workspace this Template belongs to.
template_type | Template-Type this Template belongs to.

### Create Template

```http
POST /v1/workspaces/<ID>/templates HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "name": "Template Name",
    "description": "Template description.",
		"template": {}
  }
}
```



```json
{
	"data": {
    "type": "template",
		"id": "tmp_hashhere",
		"name": "Template Name",
		"description": "Template description.",
    "is_published": false,
		"template": {},
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints create templates.

#### HTTP Request

Create template.

`POST https://api.candidio.com/v1/templates`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
workspace_id | no | Workspace, if any, this template belongs to.
industry_id | no | Industry this template belongs to.
template_type_id | no | Template-Type for this Template.
name | yes | Template name.
description | no | Describes Template.
template | yes | Production, brief, shots, etc. go here.
is_published | no | Publishes template.
editor_pick | no | Boolean
image_url | no | URL to image.

### Update Template

```http
PUT /v1/workspaces/<ID>/templates/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"description": "Updated template description.",
      "is_published": true
  }
}
```


```json
{
	"data": {
    "type": "template",
		"id": "tmp_hashhere",
		"name": "Template Name",
		"description": "Updated template description.",
    "is_published": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-06-04 09:02:07"
	}
}
```

These endpoints update templates.

#### HTTP Request

Update template.

`PUT https://api.candidio.com/v1/templates/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
workspace_id | no | Workspace, if any, this template belongs to.
industry_id | no | Industry this template belongs to.
template_type_id | no | Template-Type for this Template.
name | yes | Template name.
description | no | Describes Template.
template | yes | Production, brief, shots, etc. go here.
is_published | no | Publishes template.
editor_pick | no | Boolean
image_url | no | URL to image.

### Delete Template

```http
DELETE /v1/workspaces/<ID>/templates/<ID> HTTP/1.1
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

Delete an template.

#### HTTP Request

Delete an template.

`DELETE https://api.candidio.com/v1/templates/<ID>`
