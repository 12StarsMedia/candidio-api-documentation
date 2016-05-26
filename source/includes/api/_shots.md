
## Shots

### List Shots

```http
GET /v1/workspaces/<ID>/descriptions?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



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
