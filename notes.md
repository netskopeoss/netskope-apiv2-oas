# Speakeasy Conversion Tasks

- Need to prefix paths with folder name


## Bugs 

### Items Required for arrays in npa_publishers.json
- ERROR	validation error: [line 322] validate-types - items attribute required for arrays in OpenAPI 3.0.X documents
- ERROR	validation error: [line 351] validate-types - items attribute required for arrays in OpenAPI 3.0.X documents


### publishers_get_response in npa_publishers.json has bad schema (Doesn't match the actual response.)

- The "data" element is listed as array but it is not.


### Need to mark required parameters - examples below

- publisher post name parameter is required

### token endpoint `/infrastructure/publishers/{publisher_id}/registration_token` defined wrong. It defines the response as an array when it is just an object

- It should look like this

```
      responses:
        "200":
          description: successful operation
          content:
            application/json:
              schema:
                type: object
                properties:
                  data:
                    x-speakeasy-entity: PublisherToken
                    type: object
                    properties:
                      token:
                        type: string
                    required:
                    - token
                  status:
                    type: string
                    x-speakeasy-terraform-ignore: true
                    enum:
                      - success
                      - not found
                required:
                - data
                - status
```

### NPA Policy Rules
- RuleID is defined as int but in reality it is a string
- Access Method is defined as a string but it is an array