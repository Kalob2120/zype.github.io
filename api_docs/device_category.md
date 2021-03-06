---
layout: api
title: Zype Developer Portal | Device Categories
permalink: /api_docs/device_categories/
---

## Device Categories
<hr>
### List all Device Categories
<hr>

<pre><code>GET - https://api.zype.com/device_categories?page=page&per_page=per_page&search=search
</code></pre>

#### Parameters

Parameter | Function | Type
--------- | -------- | ----
page | The page number of records to return (zero indexed). Example: 0. | Number
per_page | The number of records to return. Example: 10. | Number
search | Performs a full text search for the term and returns records that match. Example: Mobile | String

#### Response
200
Content-Type: application/json

<pre><code>{
  "response": [
    {
      "_id": "5429b1c369702d2f7c040000",
      "_keywords": [
      "desktop"
      ],
      "created_at": "2014-09-29T15:23:47.302-04:00",
      "image_content_type": "image/png",
      "image_file_name": "desktop.png",
      "image_file_size": 19347,
      "image_fingerprint": "a661d27f5003bcf1523f75e3686f6b24",
      "image_updated_at": "2014-09-29T15:23:47.099-04:00",
      "name": "Desktop",
      "updated_at": "2014-09-29T15:23:47.302-04:00"
    },
    {
      "_id": "5429b1c469702d2f7c050000",
      "_keywords": [
      "mobile"
      ],
      "created_at": "2014-09-29T15:23:48.879-04:00",
      "image_content_type": "image/png",
      "image_file_name": "mobile.png",
      "image_file_size": 18671,
      "image_fingerprint": "070c15b95b315a6f472a6efb6c3b898c",
      "image_updated_at": "2014-09-29T15:23:48.788-04:00",
      "name": "Mobile",
      "updated_at": "2014-09-29T15:23:48.879-04:00"
    },
    {
      "_id": "5429b1c569702d2f7c060000",
      "_keywords": [
      "ott"
      ],
      "created_at": "2014-09-29T15:23:49.234-04:00",
      "image_content_type": "image/png",
      "image_file_name": "desktop.png",
      "image_file_size": 19347,
      "image_fingerprint": "a661d27f5003bcf1523f75e3686f6b24",
      "image_updated_at": "2014-09-29T15:23:49.057-04:00",
      "name": "OTT",
      "updated_at": "2014-09-29T15:23:49.234-04:00"
    },
    {
      "_id": "5429b1c569702d2f7c070000",
      "_keywords": [
      "tablet"
      ],
      "created_at": "2014-09-29T15:23:49.531-04:00",
      "image_content_type": "image/png",
      "image_file_name": "tablet.png",
      "image_file_size": 18686,
      "image_fingerprint": "8be3ee187e89cc533382bb06b6dae3ea",
      "image_updated_at": "2014-09-29T15:23:49.441-04:00",
      "name": "Tablet",
      "updated_at": "2014-09-29T15:23:49.531-04:00"
    }
  ],
  "pagination": {
    "current": 1,
    "previous": null,
    "next": null,
    "per_page": 10,
    "pages": 1
  }
}
</code></pre>

<hr>
### Retrieve a Device Category
<hr>

<pre><code>GET - https://api.zype.com/device_categories/{id}
</code></pre>

#### Parameters

Parameter | Function | Type
--------- | -------- | ----
id | String id of the Device Category to retrieve. Example: 5389352e69702d401b000000. | String

#### Response
200
Content-Type: application/json

<pre><code>{
  "response": {
    "_id": "5429b1c369702d2f7c040000",
    "_keywords": [
      "desktop"
    ],
    "created_at": "2014-09-29T15:23:47.302-04:00",
    "image_content_type": "image/png",
    "image_file_name": "desktop.png",
    "image_file_size": 19347,
    "image_fingerprint": "a661d27f5003bcf1523f75e3686f6b24",
    "image_updated_at": "2014-09-29T15:23:47.099-04:00",
    "name": "Desktop",
    "updated_at": "2014-09-29T15:23:47.302-04:00"
  }
}
</code></pre>
