## Revisions

### List Revisions
```http
GET /v1/workspaces/<ID>/productions/<ID>/revisions HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



```json
{
	"data": [{
    "type": "revision",
		"id": "rvs_hashhere",
		"instructions": "Some instructions for this revision",
		"is_open": true,
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

This endpoint a collection of paginated revisions.

#### HTTP Request

Get revisions scoped by workspace and production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/revisions`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
owner | User who created a revision.
production | Productions a revision belongs to.
workspace | Workspace a revision belongs to.
assets | Assets that belong to a revision.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
production | ID | Scope revisions by production they belong to.
user | ID | Scope revisions by user who created them.
workspace | ID | Scope revisions by workspace they belong to.

### Get Revision

```http
GET /v1/workspaces/<ID>/productions/<ID>/revisions/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



```json
{
	"data": {
    "type": "revision",
		"id": "rvs_hashhere",
		"instructions": "Some instructions for this revision",
		"is_open": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

This endpoint returns a specific revision.

#### HTTP Request

Get revision scoped by workspace and production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/revisions/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
owner | User who created a revision.
production | Productions a revision belongs to.
workspace | Workspace a revision belongs to.
assets | Assets that belong to a revision.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
production | ID | Scope revisions by production they belong to.
user | ID | Scope revisions by user who created them.
workspace | ID | Scope revisions by workspace they belong to.

### Create Revision

```http
POST /v1/workspaces/<ID>/productions/<ID>/revisions HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"instructions": "Some instructions for this revision."
  }
}
```



```json
{
	"data": {
    "type": "revision",
		"id": "rvs_hashhere",
		"instructions": "Some instructions for this revision.",
		"is_open": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:28:30"
	}
}
```

This endpoint creates a revision.

#### HTTP Request

Create a production revision.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/revisions/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
instructions | no | Revision instruction.


### Update Revision

```http
PUT /v1/workspaces/<ID>/productions/<ID>/revisions/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"instructions": "Updated instructions for this revision."
  }
}
```



```json
{
	"data": {
    "type": "revision",
		"id": "rvs_hashhere",
		"instructions": "Updated instructions for this revision.",
		"is_open": true,
    "created_at": "2016-04-04 07:28:30",
    "updated_at": "2016-04-04 07:52:41"
	}
}
```

This endpoint updates a revision.

#### HTTP Request

Update revision.

`PUT https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/revisions/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
instructions | no | Revision instruction.
