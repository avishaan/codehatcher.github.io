---
title: "SwaggerJS via Swagger-Tools for NodeJS" 
excerpt: "Learning by examples"
categories:
  - Programming
tags:
  - Programming
  - Node.js
  - Swagger.js
  - DevOps
toc: true
toc_sticky: true
---
When it comes to aligning development with devops with QA, I don't think anything comes close to SwaggerJS right now. In San Francisco, I was able to meet some of the founders to talk to them more about it. I didn't realize how big they had become but I'm not surprised. I talked about it a little in a post from 2014.

## Response with sub-properties using references

```json
"ReadOnePost": {
      "properties": {
        "_id": {
          "type": "string",
          "example": "54f44c5d26352b1b9755b12f"
        },
        "text": {
          "type": "string",
          "example": "This is a very relavent post to me",
          "description": "Text body of the post a user may create"
        },
        "logitude": {
          "type": "string",
          "example": "100.000",
          "description": "Logitude of the GPS coordinate"
        },
        "latitude": {
          "type": "string",
          "example": "100.000",
          "description": "Latitude of the GPS coordinate"
        },
        "user": {
          "description": "User information",
          "$ref": "#/definitions/ReadUserForPost"
        }
      },
```
## Response with sub-properties which is an array of objects using reference

```json
    "ReadOnePost": {
      "properties": {
        "_id": {
          "type": "string",
          "example": "54f44c5d26352b1b9755b12f"
        },
        "text": {
          "type": "string",
          "example": "This is a very relavent post to me",
          "description": "Text body of the post a user may create"
        },
        "logitude": {
          "type": "string",
          "example": "100.000",
          "description": "Logitude of the GPS coordinate"
        },
        "latitude": {
          "type": "string",
          "example": "100.000",
          "description": "Latitude of the GPS coordinate"
        },
        "images": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/ImageURL"
          }
        }
      },
      "required": ["_id"]
    },
```

## Response with sub-properties which is an array of objects NOT using reference

```json
    "CreatePost": {
      "properties": {
        "text": {
          "type": "string",
          "example": "This is a very relavent post to me",
          "description": "Text body of the post a user may create"
        },
        "longitude": {
          "type": "string",
          "example": "100.000",
          "description": "Logitude of the GPS coordinate"
        },
        "latitude": {
          "type": "string",
          "example": "100.000",
          "description": "Latitude of the GPS coordinate"
        },
        "images": {
          "type": "array",
          "items": {
            "description": "image id of images uploaded to /images route",
            "example": "554b34d8171ff19c8128c54d",
            "type": "string"
          }
        }
      },
      "required": ["text", "longitude", "latitude"]
    }
```