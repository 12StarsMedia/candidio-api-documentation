## Invites

NOTICE: This section is incomplete / in progress.

## Invite to Workspace



## Get User From Invite Code

```http
GET /v1/invites/<TOKEN> HTTP/1.1
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
		"is_confirmed": false,
		"is_invite": true,
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

Endpoint used to get information about user who is confirming an invite.

#### HTTP Request

Get user from invite code.

`GET https://api.candidio.com/v1/invites/<TOKEN>`

#### Embeddable Relationships

n/a

#### Available Scopes

n/a


## Confirm an Invite
