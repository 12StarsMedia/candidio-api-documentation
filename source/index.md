---
title: Candidio API Reference

language_tabs:
  - http: Request
  - json: Response

toc_footers:
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - api/assets
  - api/briefs
  - api/industries
  - api/productions
  - api/revisions
  - api/shots
  - api/users
  - api/video-series
  - api/workspaces
  - api/tail
  - errors

search: true
---

# Introduction

## Introduction

Welcome to the Candidio API documentation.

# Topics

## Authentication

## Nesting Models

You can embed related models and collections. Check documentation for specific relationships available on each resource. Dot notation can be used to retrieve further levels of nesting (i.e. ?inclue=workspace.users).

#### Query Parameters

Parameter | Description
--------- | -----------
include | Embed a related resource.

## Pagination

Most resources will return a paginated collection of results.

#### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
limit | 100 | Limit records returned in pagination.
page | 1 | Offset to request from pagination.

## Scoping

Most resources can be scoped by workspace and user. See list of available scopes for each resource type.

#### Query Parameters

Parameter | Description
--------- | -----------
scope | Scope by user, workspace, etc.

## Sorting

#### Query Parameters

Parameter | Description
--------- | -----------
sort | Field to order records by.
direction | Direction of sorting, `asc` or `desc`.

# Core Resources
