## Projects

### List Projects

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
PUT /v1/workspaces/<ID>/projects/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
  		"name": "Project Name Updated"
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

`PUT https://api.candidio.com/v1/projects/<ID>`

Update project scoped by workspace.

`PUT https://api.candidio.com/v1/workspaces/<ID>/projects/<ID>`

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
