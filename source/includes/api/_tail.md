## Register Account

```http
POST /v1/register HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "name": "My Company, LLC",
		"email": "normal@12starsmedia.com",
		"first_name": "Normal",
		"last_name": "Manderson"
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

Register a new Producer. Must be Administrator to access.

#### HTTP Request

Register a new Producer.

`POST https://api.candidio.com/v1/register`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
name | yes | Unique name for the workspace.
email | yes | Valid and unique email address.
first_name | yes | First name.
last_name | yes | Last name.


## Activate Account

```http
POST /v1/activate HTTP/1.1
Host: api.candidio.com
Content-Type: application/json

{
  "data": {
    "token": "token_here"
  }
}
```

```json
{
	"success": {
		"http_code": 200,
		"message": "Success"
	}
}
```

Public. Activate an account.

#### HTTP Request

Activate account with confirmation code.

`POST https://api.candidio.com/v1/activate`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
token | yes | Confirmation code/token.

## Request Password Reset Email

```http
POST /v1/users/forgot-password HTTP/1.1
Host: api.candidio.com
Content-Type: application/json

{
  "data": {
    "email": "email"
  }
}
```

```json
{
	"success": {
		"http_code": 200,
		"message": "Success"
	}
}
```

Request email with password reset link.

#### HTTP Request

Forgotten password reset route.

`POST https://api.candidio.com/v1/users/forgot-password`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
email | yes | Producer account email.


## Reset Password with Token

```http
POST /v1/users/reset-password HTTP/1.1
Host: api.candidio.com
Content-Type: application/json

{
  "data": {
    "password": "new_password",
    "token": "token_here"
  }
}
```

```json
{
	"success": {
		"http_code": 200,
		"message": "Success"
	}
}
```

Reset password.

#### HTTP Request

Reset password with token.

`POST https://api.candidio.com/v1/users/forgot-password`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
password | yes | New password to set.
token | yes | Token received from v1/users/forgot-password email.


## Confirm Email Update

```http
POST /v1/users/confirm-email HTTP/1.1
Host: api.candidio.com
Content-Type: application/json

{
  "data": {
    "token": "token_here"
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
		"email": "normals_new_email@12starsmedia.com",
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

Confirm change of email.

#### HTTP Request

Use token to confirm update to new email address.

`POST https://api.candidio.com/v1/users/confirm-email`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
token | yes | Token received in email when updating email on user.


## Update User Details

## Update Workspace Details

## Industries
