

This operation receives 2 images: front view of the identity document and a frontal photograph (selfie) of the end-user. This operation gives as a result a similarity percentage (score) between the frontal photo in the identification document and the fontal photograph of the end-user. 

## Startup request

- Endpoint: `https://onboardingtest.did.cyxtera.com/v1/face-matching`

- HTTP Method: `POST`  
- Header: `x-api-key`
    - Api-key value of the secured entity. This value is unique for each entity and is managed by Cyxtera.  
- Body:

        {
            "sourceImage": "base64",
            "targetImage": "base64",
            "operations":["FACE_MATCHING"]
        }

- Successful result:

        {
          "data": {
            "processId": uuid
          }
        }

- Unsuccessful result:

        {
          "status":400,
          "code": "FACIN001",
          "message": "Required parameter missing"
        }


## Process validation request  

- Endpoint: `https://onboardingtest.did.cyxtera.com/v1/face-matching/{processId}`
- HTTP Method: `GET`
- Header: `x-api-key`
    - Api-key value of the secured entity. This value is unique for each entity and is managed by Cyxtera.  
- Successful result:

        {
        "data": {
        "faceMatching": {
            "score": 97.13,
            "status": "200"
                }
            }
        }

- Unsuccessful result:

        {
        "data": {
            "faceMatching": {
                "status":400,
                "code": "FACIN001",
                "message": "Required parameter missing"
                    }
                }
        }

## Error codes
| <div style="width:120px">**General HTTP code**</div> | <div style="width:85px">**Specific code**</div> | <div style="width:145px">**Description**</div> | <div style="width:145px">**Message**</div> |
| -------------- | ----------------- | --------- | ---- |
| 400 | FACIN001 | The required parameter was not sent. | Parameter `[PARAMETER]` not found |
| 400 | FACIN002 | The document photograph was not sent in Base64 format. | Document image is not a valid base64 string. |
| 400 | FACIN003 | The user´s selfie was not sent in Base64 format. | Selfie image is not a valid base64 string. |
| 422 | FACPR001 | It is not possible to find a face in the provided pictures. | Face not found. |
| 404 | FACOU001 | **1.** A process cannot be found in the provided parameters. <br /> **2.** The *apikeyId* does not match the one n the database. | Process not found. |