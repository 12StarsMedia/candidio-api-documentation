## Users

### List Users

```http
GET /v1/users?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": [{
    "type": "users",
		"id": "usr_hashhere",
		"user_hash": "hashhere",
		"avatar": {
			"color": "2B8ACA",
			"image_urls": {
				"compact": null,
				"compact_hd": null,
				"normal": null,
				"normal_hd": null,
				"large": null
			}
		},
		"email": "normal@12starsmedia.com",
		"full_name": "Normal Manderson",
		"first_name": "Normal",
		"last_name": "Manderson",
		"is_confirmed": true,
		"is_invite": false,
		"is_beta": false,
		"preferences": {
			"notifications": {
				"project_production_changes": {
					"in_app": true,
					"email": true
				},
				"something_shared_with_me": {
					"in_app": true,
					"email": true
				},
				"messages": {
					"in_app": true,
					"email": true
				},
				"workspace_changes": {
					"in_app": true,
					"email": true
				}
			},
			"avatar": {
				"color": "2B8ACA"
			}
		},
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

These endpoints return a collection of paginated users.

#### HTTP Request

Get users.

`GET https://api.candidio.com/v1/users`

Get users scoped by workspace.

`GET https://api.candidio.com/v1/workspace/<ID>/users`

Get users scoped by workspace and production.

`GET https://api.candidio.com/v1/workspace/<ID>/productions/<ID>/users`

Get users scoped by workspace and project.

`GET https://api.candidio.com/v1/workspace/<ID>/video-series/<ID>/users`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
workspaces | Workspaces a user is a member of.
owned_productions | Productions the user created.
shared_productions | Productions shared with a user.
owned_video_series | Video Series the user created.
shared_video_series | Video Series shared with the user.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
production | ID | Scope by ability to view production.
project | ID | Scope by ability to view project.
workspace | ID | Scope by workspace membership.

### Get a Specific User

```http
GET /v1/users/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": {
		"type": "users",
		"id": "usr_hashhere",
		"user_hash": "hashhere",
		"avatar": {
			"color": "2B8ACA",
			"image_urls": {
				"compact": null,
				"compact_hd": null,
				"normal": null,
				"normal_hd": null,
				"large": null
			}
		},
		"email": "normal@12starsmedia.com",
		"full_name": "Normal Manderson",
		"first_name": "Normal",
		"last_name": "Manderson",
		"is_confirmed": true,
		"is_invite": false,
		"is_beta": false,
		"preferences": {
			"notifications": {
				"project_production_changes": {
					"in_app": true,
					"email": true
				},
				"something_shared_with_me": {
					"in_app": true,
					"email": true
				},
				"messages": {
					"in_app": true,
					"email": true
				},
				"workspace_changes": {
					"in_app": true,
					"email": true
				}
			},
			"avatar": {
				"color": "2B8ACA"
			}
		},
		"created_at": "2015-10-28 19:32:03",
		"updated_at": "2015-10-28 19:32:03"
	}
}
```

These endpoints return a specific user.

#### HTTP Request

Get user.

`GET https://api.candidio.com/v1/users/<ID>`

Get user scoped by workspace.

`GET https://api.candidio.com/v1/workspace/<ID>/users/<ID>`

Get user scoped by workspace and production.

`GET https://api.candidio.com/v1/workspace/<ID>/productions/<ID>/users/<ID>`

Get user scoped by workspace and project.

`GET https://api.candidio.com/v1/workspace/<ID>/video-series/<ID>/users/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
workspaces | Workspaces a user is a member of.
owned_productions | Productions the user created.
shared_productions | Productions shared with a user.
owned_video_series | Video Series the user created.
shared_video_series | Video Series shared with the user.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
production | ID | Scope by ability to view production.
project | ID | Scope by ability to view project.
workspace | ID | Scope by workspace membership.


### Create User

```http
POST /v1/users HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "first_name": "Normal",
    "last_name": "Manderson",
		"email": "normal@12starsmedia.com",
		"password": "password"
  }
}
```

```json
{
	"data": {
		"type": "users",
		"id": "usr_hashhere",
		"user_hash": "hashhere",
		"avatar": {
			"color": "2B8ACA",
			"image_urls": {
				"compact": null,
				"compact_hd": null,
				"normal": null,
				"normal_hd": null,
				"large": null
			}
		},
		"email": "normal@12starsmedia.com",
		"full_name": "Normal Manderson",
		"first_name": "Normal",
		"last_name": "Manderson",
		"is_confirmed": true,
		"is_invite": false,
		"is_beta": false,
		"preferences": {
			"notifications": {
				"project_production_changes": {
					"in_app": true,
					"email": true
				},
				"something_shared_with_me": {
					"in_app": true,
					"email": true
				},
				"messages": {
					"in_app": true,
					"email": true
				},
				"workspace_changes": {
					"in_app": true,
					"email": true
				}
			},
			"avatar": {
				"color": "2B8ACA"
			}
		},
		"created_at": "2015-10-28 19:32:03",
		"updated_at": "2015-10-28 19:32:03"
	}
}
```

This endpoint creates a new user for an authorized user.

#### HTTP Request

Create user.

`POST https://api.candidio.com/v1/users`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
email | yes | Valid and unique email address.
password | yes | Password of more than 8 characters.
first_name | yes | First name.
last_name | yes | Last name.

### Update User

```http
PUT /v1/users/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "first_name": "Guy"
  }
}
```

```json
{
	"data": {
		"type": "users",
		"id": "usr_hashhere",
		"user_hash": "hashhere",
		"avatar": {
			"color": "2B8ACA",
			"image_urls": {
				"compact": null,
				"compact_hd": null,
				"normal": null,
				"normal_hd": null,
				"large": null
			}
		},
		"email": "normal@12starsmedia.com",
		"full_name": "Guy Manderson",
		"first_name": "Guy",
		"last_name": "Manderson",
		"is_confirmed": true,
		"is_invite": false,
		"is_beta": false,
		"preferences": {
			"notifications": {
				"project_production_changes": {
					"in_app": true,
					"email": true
				},
				"something_shared_with_me": {
					"in_app": true,
					"email": true
				},
				"messages": {
					"in_app": true,
					"email": true
				},
				"workspace_changes": {
					"in_app": true,
					"email": true
				}
			},
			"avatar": {
				"color": "2B8ACA"
			}
		},
		"created_at": "2015-10-28 19:32:03",
		"updated_at": "2015-10-29 00:08:06"
	}
}
```

Update a user.

#### HTTP Request

Update user.

`PUT https://api.candidio.com/v1/users/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
email | no | Valid and unique email address.
password | no | Old password. Required with `new_password`.
new_password | no | Password of more than 8 character.
first_name | no | First name.
last_name | no | Last name.
is_beta | no | Boolean. Administrator only.
preferences | no | Array of preferences.
preferences.project_production_changes.in_app | no | Boolean.
preferences.project_production_changes.email | no | Boolean.
preferences.something_shared_with_me.in_app | no | Boolean.
preferences.something_shared_with_me.email | no | Boolean.
preferences.messages.in_app | no | Boolean.
preferences.messages.email | no | Boolean.
preferences.workspace_changes.in_aps | no | Boolean.
preferences.workspace_changes.email | no | Boolean.
preferences.avatar.color | no | String, hexadecimal color code.

### Delete User

```http
DELETE /v1/users/<ID> HTTP/1.1
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

Delete a user.

#### HTTP Request

Delete a user.

`DELETE https://api.candidio.com/v1/users/<ID>`
