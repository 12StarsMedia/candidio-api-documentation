## Workspaces

### List Workspaces

```http
GET /v1/workspaces?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```



```json
{
	"data": [{
    "type": "workspaces",
		"id": "wrk_hashhere",
    "organization_name": "Stehr, Kunze and Kerluke",
    "workspace_name": "Stehr, Kunze and Kerluke",
    "workspace_path": "stehr, kunze and kerluke",
    "phone": null,
    "is_invite": null,
    "stripe_id": null,
    "card_brand": "visa",
    "card_last_four": 4242,
    "features": {
      "video_series": false,
      "users": 1,
      "coachingPlatform": "Limited",
      "templates": "Limited",
      "stockLibrary": false,
      "landingPage": false,
      "help_center": true,
      "in_app_chat": true,
      "priority_emails": false,
      "phone_support": false
    },
    "internal_notes": "",
    "account": 470000,
    "created_at": "2015-10-10 04:11:13",
    "updated_at": "2016-04-07 09:51:58"
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

Get workspaces.

`GET https://api.candidio.com/v1/workspaces`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
assets | My Brand/Stock Library assets belonging to a workspace.
descriptions | Shot descriptions. Depreciated.
invites | Invitations to collaborate on workspace.
productions | Productions belonging to a workspace.
video_series | Video Series belonging to a workspace.
roles | Roles available on workspace. Includes custom roles.
subscriptions | Stripe subscriptions workspace has.
industry | Industry assigned to a workspace.
users | Users who belong to a workspace.
template_collection | Template collection assigned to a workspace.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
user | ID | Scope workspaces by user's access.

### Get a Specific Workspace

```http
GET /v1/workspaces/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

```json
{
	"data": {
    "type": "workspace",
		"id": "wrk_hashhere",
    "organization_name": "Stehr, Kunze and Kerluke",
    "workspace_name": "Stehr, Kunze and Kerluke",
    "workspace_path": "stehr, kunze and kerluke",
    "phone": null,
    "is_invite": null,
    "stripe_id": null,
    "card_brand": "visa",
    "card_last_four": 4242,
    "features": {
      "video_series": false,
      "users": 1,
      "coachingPlatform": "Limited",
      "templates": "Limited",
      "stockLibrary": false,
      "landingPage": false,
      "help_center": true,
      "in_app_chat": true,
      "priority_emails": false,
      "phone_support": false
    },
    "internal_notes": "",
    "account": 470000,
    "created_at": "2015-10-10 04:11:13",
    "updated_at": "2016-04-07 09:51:58"
	}
}
```

These endpoints return a specific workspace.

#### HTTP Request

Get workspace.

`GET https://api.candidio.com/v1/workspaces/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
assets | My Brand/Stock Library assets belonging to a workspace.
descriptions | Shot descriptions. Depreciated.
invites | Invitations to collaborate on workspace.
productions | Productions belonging to a workspace.
video_series | Video Series belonging to a workspace.
roles | Roles available on workspace. Includes custom roles.
subscriptions | Stripe subscriptions workspace has.
industry | Industry assigned to a workspace.
users | Users who belong to a workspace.
template_collection | Template collection assigned to a workspace.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
user | ID | Scope workspaces by user's access.


### Create Workspace

```http
POST /v1/workspaces HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "is_business": true,
    "company": "My Company, LLC"
  }
}
```



```json
{
	"data": {
    "type": "workspace",
		"id": "wrk_hashhere",
    "organization_name": "My Company, LLC",
    "workspace_name": "My Company, LLC",
    "workspace_path": "my-company-llc",
    "phone": null,
    "is_invite": null,
    "stripe_id": null,
    "card_brand": null,
    "card_last_four": null,
    "features": {
      "video_series": false,
      "users": 1,
      "coachingPlatform": "Limited",
      "templates": "Limited",
      "stockLibrary": false,
      "landingPage": false,
      "help_center": true,
      "in_app_chat": true,
      "priority_emails": false,
      "phone_support": false
    },
    "internal_notes": "",
    "account": 0,
    "created_at": "2015-10-10 04:11:13",
    "updated_at": "2016-04-07 09:51:58"
	}
}
```

This endpoint creates a new workspace for an authorized user.

#### HTTP Request

Create workspace.

`POST https://api.candidio.com/v1/workspaces`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
organization | no | Name of organization for workspace.
name | no | Unique name for the workspace.
path | no | Depreciated: URL slug for workspace.
phone | no | Workspace phone number.
is_business | yes | Boolean for business or personal workspace.
internal_notes | no | Internal notes for administrators.

### Update Workspace

```http
PUT /v1/workspaces/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
    "name": "My Company Renamed, LLC"
  }
}
```

```json
{
	"data": {
    "type": "workspace",
		"id": "wrk_hashhere",
    "organization_name": "My Company Renamed, LLC",
    "workspace_name": "My Company Renamed, LLC",
    "workspace_path": "my-company-renamed-llc",
    "phone": null,
    "is_invite": null,
    "stripe_id": null,
    "card_brand": null,
    "card_last_four": null,
    "features": {
      "video_series": false,
      "users": 1,
      "coachingPlatform": "Limited",
      "templates": "Limited",
      "stockLibrary": false,
      "landingPage": false,
      "help_center": true,
      "in_app_chat": true,
      "priority_emails": false,
      "phone_support": false
    },
    "internal_notes": "",
    "account": 0,
    "created_at": "2015-10-10 04:11:13",
    "updated_at": "2016-04-07 09:51:58"
	}
}
```

Update a workspace.

#### HTTP Request

Update workspace.

`PUT https://api.candidio.com/v1/workspaces/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
organization | no | Name of company.
name | no | Name of workspace.
path | no | URL slug for workspace. Depreciated.
phone | no | Contact number for workspace manager.
template_collection_id | no | Update workspace template collection. Administrators only.
industry_id | no | Update workspace industry. Users with workspaces.update permission only.
internal_notes | no | Workspace notes for internal usage. Administrators only.
features | no | Array. Update workspace features. Administrators only.
features.video_series | no | Boolean. Enables video_series on a workspace.
features.users | no | Integer. Maximum number of Co-Producers allowed to collaborate.
features.coachingPlatform | no | String. Type of coaching platform.
features.templates | no | String. Templates allowed.
features.stockLibrary | no | Boolean. Enables My Brand/Stock Library on a workspace.
features.landingPage | no | Boolean.
features.help_center | no | Boolean.
features.in_app_chat | no | Boolean.
features.priority_emails | no | Boolean.
features.phone_support | no | Boolean.

### Delete Workspace

```http
DELETE /v1/workspaces/<ID> HTTP/1.1
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

Delete a workspace (also unsubscribes account).

#### HTTP Request

Delete a workspace.

`DELETE https://api.candidio.com/v1/workspaces/<ID>`

# Account

## Create Account

Create a new workspace with attached new user account.

This is a public route and authorization is not necessary.

```http
POST https://api.candidio.com/v1/register HTTP/1.1
Origin: https://api.candidio.com
Content-Type: application/json

{
"data": {
"first_name": "Test",
"last_name": "McTestface",
"email": "producer@candidio.com",
"password": "can-test",
"is_business": false,
"company": "McTestface Studios"
}
}
```
> All fields required unless `is_business` is set to `false`, in which case `company` becomes optional.
