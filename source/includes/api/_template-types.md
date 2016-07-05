## Template-Types

### List Template-Types

```http
GET /v1/template-types?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": [{
    "type": "template_type",
		"id": "tpt_hashhere",
		"name": "Template Name",
		"description": "Template description.",
		"icon": "http:\/\/example.com",
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

These endpoints return a collection of paginated template-types.

#### HTTP Request

Get template-types.

`GET https://api.candidio.com/v1/template-types`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
templates | Templates belonging to this Template-Type.

### Get a Specific Template

```http
GET /v1/template-types/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": {
    "type": "template_type",
		"id": "tpt_hashhere",
		"name": "Template Name",
		"description": "Template description.",
		"icon": "http:\/\/example.com",
    "is_published": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints return a specific template-type.

#### HTTP Request

Get template-type.

`GET https://api.candidio.com/v1/template-types/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
templates | Templates belonging to this Template-Type.

### Create Template

```http
POST /v1/workspaces/<ID>/template-types HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "name": "Template Name",
    "description": "Template description.",
		"icon": "http:\/\/example.com"
  }
}
```



```json
{
	"data": {
    "type": "template_type",
		"id": "tpt_hashhere",
		"name": "Template Name",
		"description": "Template description.",
		"icon": "http:\/\/example.com",
    "is_published": false,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints create template-types.

#### HTTP Request

Create template-type.

`POST https://api.candidio.com/v1/template-types`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
name | yes | Template-Type name.
description | no | Describes Template-Type.
icon | no | URL to image for this Template-Type.
is_published | no | Publishes Template-Type.

### Update Template

```http
PUT /v1/workspaces/<ID>/template-types/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"description": "Updated template-type description.",
      "is_published": true
  }
}
```


```json
{
	"data": {
    "type": "template_type",
		"id": "tpt_hashhere",
		"name": "Template Name",
		"description": "Updated template-type description.",
		"icon": "http:\/\/example.com",
    "is_published": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-06-04 09:02:07"
	}
}
```

These endpoints update template-types.

#### HTTP Request

Update template-type.

`PUT https://api.candidio.com/v1/template-types/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
name | yes | Template-Type name.
description | no | Describes Template-Type.
icon | no | URL to image for this Template-Type.
is_published | no | Publishes Template-Type.

### Delete Template

```http
DELETE /v1/workspaces/<ID>/template-types/<ID> HTTP/1.1
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

Delete an template-type.

#### HTTP Request

Delete an template-type.

`DELETE https://api.candidio.com/v1/template-types/<ID>`
