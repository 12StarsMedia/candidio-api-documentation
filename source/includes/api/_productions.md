## Productions

### List Productions

```http
GET /v1/workspaces/<ID>/productions?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



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
created_by | Person who created a production.
project | Project production belongs to, if any.
template | Template production was created from, if any.
workspace | Workspace a production belongs to.
assets | Assets attached to a production.
briefs | All briefs attached to a production.
descriptions | Shot descriptions attached to a production.
collaborators | Users a production has been shared with.
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

### Get Production

```http
GET /v1/workspaces/<ID>/productions/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



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
created_by | Person who created a production.
project | Project production belongs to, if any.
template | Template production was created from, if any.
workspace | Workspace a production belongs to.
assets | Assets attached to a production.
briefs | All briefs attached to a production.
descriptions | Shot descriptions attached to a production.
collaborators | Users a production has been shared with.
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

{
  "data": {
		"title": "Title of Production",
		"goal_date": "2016-04-16 00:00:00"
  }
}
```



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
