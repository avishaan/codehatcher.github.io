---
title: "Swagger 2.0 Spec File Upload Method" 
excerpt: "A little information on how to edit your swagger.json document (v2) so that you can accept file uploads in NodeJS. Includes a workaround for a current bug."
categories:
  - programming
tags:
  - programming
  - Swagger.js
toc: true
toc_sticky: true
---
I have searched far and near for how to write your Swagger doc to allow a file upload. They are usually for the "1.2" spec but sometimes they are incorrect as well.

The following snippet will allow you to send a file which will be in `req.body.files.file` (when using [multner](https://www.npmjs.org/package/multer#readme))

```javascript

  "/v1/images": {
    post: {
      x-swagger-router-controller: "images",
      operationId: "createImage",
      tags: ["images"],
      description: "Upload image",
      consumes: [
        "multipart/form-data",
        "application/x-www-form-urlencoded"
      ],
      parameters: [
        {
          name: "file",
          in: "formData",
          type: "file",
          description: "Image information",
          required: true
        }
      ],
      responses: {
        default: {
          description: "Invalid request.",
          schema: {
            "$ref": "Error"
          }
        },
        200: {
          description: "Successful request.",
          schema: {
            id: "string"
          }
        }
      }
    }
  }

```

### Current Issue and Workaround
Currently, there is a problem preventing the official swagger-ui to work with the above swagger JSON. Until then a workaround is below. You can track the status of this issue [on GitHub](https://github.com/swagger-api/swagger-ui/issues/662) and when that is fixed you can use the above code instead.

```javascript
    "/v1/images": {
      post: {
        x-swagger-router-controller: "images",
        operationId: "createImage",
        tags: ["images"],
        description: "Upload image",
        consumes: [
          "multipart/form-data",
          "application/x-www-form-urlencoded"
        ],
        parameters: [
          {
            name: "file",
            in: "formData",
            type: "string",
            description: "Image information",
            required: true
          }
        ],
        responses: {
          default: {
            description: "Invalid request.",
            schema: {
              $ref: "Error"
            }
          },
          200: {
            description: "Successful request.",
            schema: {
              id: "string"
            }
          }
        }
      }
    }
```