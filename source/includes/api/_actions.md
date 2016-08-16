## Actions

### List Actions

```http
GET /v1/actions?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": [{
    "type": "actions",
		"id": "act_hashhere",
		"created_at": "2015-10-28 19:32:03",
		"updated_at": "2015-10-28 19:32:03"
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

These endpoints return a collection of paginated actions.

#### HTTP Request

Get actions.

`GET https://api.candidio.com/v1/actions`

Get actions scoped by user.

`GET https://api.candidio.com/v1/users/<ID>/actions`

Get actions scoped by workspace.

`GET https://api.candidio.com/v1/workspace/<ID>/actions`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
actionable | Resource model affected by this action.
user | User who performed this action.
workspace | Workspace this action belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
user | ID | Scope by user action belongs to.
workspace | ID | Scope by workspace action belongs to.
