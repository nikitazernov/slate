---
title: Recognito API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Recognito Server API Reference! Use this page as a reference when building apps around Recognito Server.

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

<aside class="notice">
Authentication will be added in future releases.
</aside>

# Face Recognition

## Validate Picture

```shell
curl -X POST "http://x.x.x.x/api/validate\
?hash=md5_hash_of_image" \
    -H "Content-Type: application/octet-stream" \
    --data-raw "$body"
```

> The above command returns JSON structured like this:

```json
{
  "verification":
  {
    "image": "Given Hash",
    "faces": 1
  },
  "faceIds": [ "9dc3670d-1c20-4135-adbd-3f0ba77ac0a1" ]
}
```

This endpoint validates picture on face presence.

### HTTP Request

`POST http://x.x.x.x/api/validate`

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
hash | False | MD5 hash of given image.

<aside class="warning">
Image contained in body should be only JPEG!
</aside>

## Identify Image

```shell
curl -X POST "http://x.x.x.x/api/identify" \
    -H "Content-Type: application/json; charset=utf-8" \
    --data-raw "$body"
```

> The above command returns JSON structured like this:

```json
{
  "confidence": 0.12345
}
```

This endpoint identifies person in the database by image.

### HTTP Request

`POST http://x.x.x.x/api/identify`

### Body Parameters

Parameter | Description
--------- | -----------
faceIds | An array of face Ids returned by `verify` endpoint.

### Body Example

```json
{
  "faceIds": [ "9dc3670d-1c20-4135-adbd-3f0ba77ac0a1" ]
}
```