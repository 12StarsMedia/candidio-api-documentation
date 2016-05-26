## Industries

### List Industries

```http
GET /v1/industries?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



```json
{
	"data": [{
    "type": "industry",
		"id": "ind_hashhere",
		"name": "Industry Name",
		"description": "Industry description.",
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

These endpoints return a collection of paginated industries.

#### HTTP Request

Get industries.

`GET https://api.candidio.com/v1/industries`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
templates | Templates that belong to this industry.
workspaces | Workspaces that belong to this industry

### Get a Specific Industry

```http
GET /v1/industries/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



```json
{
	"data": {
    "type": "industry",
		"id": "ind_hashhere",
		"name": "Industry Name",
		"description": "Industry description.",
    "is_published": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints return a specific industry.

#### HTTP Request

Get industry.

`GET https://api.candidio.com/v1/industries/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
templates | Templates that belong to this industry.
workspaces | Workspaces that belong to this industry.

### Create Industry

```http
POST /v1/workspaces/<ID>/industries HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "name": "Industry Name",
    "description": "Industry description."
  }
}
```



```json
{
	"data": {
    "type": "industry",
		"id": "ind_hashhere",
		"name": "Industry Name",
		"description": "Industry description.",
    "is_published": false,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

These endpoints create industries.

#### HTTP Request

Create industry.

`POST https://api.candidio.com/v1/industries`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
name | yes | Industry name.
description | no | Industry description.
is_published | no | Publishes industry.

### Update Industry

```http
PUT /v1/workspaces/<ID>/industries/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"description": "Updated industry description.",
      "is_published": true
  }
}
```



```json
{
	"data": {
    "type": "industry",
		"id": "ind_hashhere",
		"name": "Industry Name",
		"description": "Updated industry description.",
    "is_published": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-06-04 09:02:07"
	}
}
```

These endpoints update industries.

#### HTTP Request

Update industry.

`PUT https://api.candidio.com/v1/industries/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
name | yes | Industry name.
description | no | Industry description.
is_published | no | Publishes industry.

### Delete Industry

```http
DELETE /v1/workspaces/<ID>/industries/<ID> HTTP/1.1
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

Delete an industry.

#### HTTP Request

Delete an industry.

`DELETE https://api.candidio.com/v1/industries/<ID>`
