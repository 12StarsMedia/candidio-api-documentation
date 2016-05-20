## Briefs

### List Briefs

```http
GET /v1/workspaces/<ID>/productions/<ID>/briefs?limit=100 HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": [{
    "type": "brief",
		"id": "brf_hashhere",
		"purpose": "purpose description",
		"purpose_because": "purpose because desription",
		"description": null,
		"end_screen": null,
		"instructions": null,
		"meta": {
			"length": "3.0",
			"tone": {
				"action": false,
				"brief": false,
				"clean": false,
				"clever": false,
				"cool": false,
				"emotional": false,
				"fancy": false,
				"fast": false,
				"fresh": false,
				"fun": false,
				"funny": false,
				"happy": false,
				"inspiring": false,
				"inviting": false,
				"long": false,
				"mysterious": false,
				"powerful": false,
				"serious": false,
				"slow": false,
				"thoughtProvoking": false
			},
			"music": false,
			"musicType": null,
			"musicProvider": null,
			"videoType": "Other"
		},
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

This endpoint returns a collection of paginated briefs.

#### HTTP Request

Briefs route to get paginated collection scoped by workspace and production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
production | Production the brief belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
user | ID | Scope assets by user that created them.
workspace | ID | Scope assets by workspace they belong to.

### Get Brief

```http
GET /v1/workspaces/<ID>/productions/<ID>/briefs/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "brief",
		"id": "brf_hashhere",
		"purpose": "purpose description",
		"purpose_because": "purpose because desription",
		"description": null,
		"end_screen": null,
		"instructions": null,
		"meta": {
			"length": "3.0",
			"tone": {
				"action": false,
				"brief": false,
				"clean": false,
				"clever": false,
				"cool": false,
				"emotional": false,
				"fancy": false,
				"fast": false,
				"fresh": false,
				"fun": false,
				"funny": false,
				"happy": false,
				"inspiring": false,
				"inviting": false,
				"long": false,
				"mysterious": false,
				"powerful": false,
				"serious": false,
				"slow": false,
				"thoughtProvoking": false
			},
			"music": false,
			"musicType": null,
			"musicProvider": null,
			"videoType": "Other"
		},
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
	},
}
```

This endpoint returns a collection of paginated briefs.

#### HTTP Request

Retrieve a specific brief scoped by workspace and production.

`GET https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs/<ID>`

#### Embeddable Relationships

Relationship | Description
------------ | -----------
production | Production the brief belongs to.

#### Available Scopes

Scope | Argument | Description
----- | -------- | -----------
user | ID | Scope assets by user that created them.
workspace | ID | Scope assets by workspace they belong to.

### Create Brief

```http
POST /v1/workspaces/<ID>/productions/<ID>/briefs HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
		"purpose": "purpose description",
		"purpose_because": "purpose because description"
  }
}
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "brief",
		"id": "brf_hashhere",
		"purpose": "purpose description",
		"purpose_because": "purpose because description",
		"description": null,
		"end_screen": null,
		"instructions": null,
		"meta": {
			"length": "3.0",
			"tone": {
				"action": false,
				"brief": false,
				"clean": false,
				"clever": false,
				"cool": false,
				"emotional": false,
				"fancy": false,
				"fast": false,
				"fresh": false,
				"fun": false,
				"funny": false,
				"happy": false,
				"inspiring": false,
				"inviting": false,
				"long": false,
				"mysterious": false,
				"powerful": false,
				"serious": false,
				"slow": false,
				"thoughtProvoking": false
			},
			"music": false,
			"musicType": null,
			"musicProvider": null,
			"videoType": "Other"
		},
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
	},
}
```

Create a brief.

#### HTTP Request

Create a brief for a specific workspace and production.

`POST https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
purpose | no | "People who watch this video will..."
purpose_because | no | "because I show and tell them..."
description | no | Brief description.
end_screen | no | End screen instructions.
instructions | no | Additional instructions.
meta | no | Array of brief meta data.
meta.length | no | Desired running time of final production.
meta.tone | no | Array of tone options.
meta.tone.action | no | ...
meta.tone.brief | no | ...
meta.tone.clean | no | ...
meta.tone.clever | no | ...
meta.tone.cool | no | ...
meta.tone.emotional | no | ...
meta.tone.fancy | no | ...
meta.tone.fast | no | ...
meta.tone.fresh | no | ...
meta.tone.fun | no | ...
meta.tone.funny | no | ...
meta.tone.happy | no | ...
meta.tone.inspiring | no | ...
meta.tone.inviting | no | ...
meta.tone.long | no | ...
meta.tone.mysterious | no | ...
meta.tone.powerful | no | ...
meta.tone.serious | no | ...
meta.tone.slow | no | ...
meta.tone.thoughtProvoking | no | ...
meta.videoType | no | ...
meta.musicProvider | no | ...
meta.musicType | no | ...
meta.music | no | ...

### Update Brief

```http
PUT /v1/workspaces/<ID>/productions/<ID>/briefs/<ID> HTTP/1.1
Host: api.candidio.com
Content-Type: application/json
Authorization: Bearer n8P1vbHYYsznzb25oO3PiePEnLzaeRhdq7Zk8YUJ

{
  "data": {
		"purpose": "purpose description updated"
  }
}
```

> The above command returns JSON structured like this:

```json
{
	"data": {
    "type": "brief",
		"id": "brf_hashhere",
		"purpose": "purpose description updated",
		"purpose_because": "purpose because description",
		"description": null,
		"end_screen": null,
		"instructions": null,
		"meta": {
			"length": "3.0",
			"tone": {
				"action": false,
				"brief": false,
				"clean": false,
				"clever": false,
				"cool": false,
				"emotional": false,
				"fancy": false,
				"fast": false,
				"fresh": false,
				"fun": false,
				"funny": false,
				"happy": false,
				"inspiring": false,
				"inviting": false,
				"long": false,
				"mysterious": false,
				"powerful": false,
				"serious": false,
				"slow": false,
				"thoughtProvoking": false
			},
			"music": false,
			"musicType": null,
			"musicProvider": null,
			"videoType": "Other"
		},
		"created_at": "2016-04-08 09:08:25",
		"updated_at": "2016-04-08 09:08:25"
	},
}
```

Update a brief.

#### HTTP Request

Update a brief for a specific workspace and production.

`PUT https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs/<ID>`

#### JSON Payload Parameters

Parameter | Required | Description
--------- | -------- | -----------
purpose | no | "People who watch this video will..."
purpose_because | no | "because I show and tell them..."
description | no | Brief description.
end_screen | no | End screen instructions.
instructions | no | Additional instructions.
meta | no | Array of brief meta data.
meta.length | no | Desired running time of final production.
meta.tone | no | Array of tone options.
meta.tone.action | no | ...
meta.tone.brief | no | ...
meta.tone.clean | no | ...
meta.tone.clever | no | ...
meta.tone.cool | no | ...
meta.tone.emotional | no | ...
meta.tone.fancy | no | ...
meta.tone.fast | no | ...
meta.tone.fresh | no | ...
meta.tone.fun | no | ...
meta.tone.funny | no | ...
meta.tone.happy | no | ...
meta.tone.inspiring | no | ...
meta.tone.inviting | no | ...
meta.tone.long | no | ...
meta.tone.mysterious | no | ...
meta.tone.powerful | no | ...
meta.tone.serious | no | ...
meta.tone.slow | no | ...
meta.tone.thoughtProvoking | no | ...
meta.videoType | no | ...
meta.musicProvider | no | ...
meta.musicType | no | ...
meta.music | no | ...

### Delete Brief

```http
DELETE /v1/workspaces/<ID>/productions/<ID>/briefs/<ID> HTTP/1.1
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

Delete a brief.

#### HTTP Request

Delete a brief, scoped by workspace and production.

`DELETE https://api.candidio.com/v1/workspaces/<ID>/productions/<ID>/briefs/<ID>`
