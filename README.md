

## ANCPI ePay integration API

------------------------------------------------------------------------------------------

#### Search ANCPI Land Registry information

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/searchImobil</b></code> <code>Search ANCPI electronic database by any type of identifier</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |


##### Headers

> | Key      | Value               | description                                                           |
> |----------|---------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | judet      |  required | String   | County - From value list  |
> | uat      |  required | String   | Administrative unit - From value list  |
> | cautare      |  required | String   | Numar CF/Cad/Topo/Electronic  |

###### Example
```bash
curl -L 'https://$uri/api/partners/searchImobil' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' \
-H 'Content-Type: application/json' \
-d '{
    "judet":"Dâmbovița",
    "uat":"Tartasesti",
    "cautare":"12345"
}'
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)    |
> | `401`         | `text/html;charset=utf-8`         | None  |


##### Response Body

> | name        |   data type  | description                                       |
> |-------------|--------------|---------------------------------------------------|
> | status      |   String   | <ul><li>"OK" - search term is found in ANCPI database</li><li>"WARN" - search term not found in ANCPI database</li><li>"ERROR" - error searching ANCPI database (see code)</li></ul>  |
> | code      |   String   | From value list |
> | result    | Array | Result Object |

###### Example
```json
{
    "status": "OK",
    "code": "VALIDATION_SUCCESS"
    "result": [
        {
            "identificator": "228793",
            "tip": "Teren",
            "suprafata": null,
            "stare": "Activa",
            "graficGeoportal": "https://geoportal.ancpi.ro/imobile_lookup.html?immovableid=25528271",
            "adresa": "Judet:BUCURESTI, Uat:Bucuresti Sectorul 3, Loc:Bucuresti Sectorul 3, Str:ROMULUS, Nr:38",
            "nrVechiCarteFunciara": "6346",
            "nrVechiCadastral": "4484",
            "nrTopografic": "3165/34/4/2"
        }
    ]
}
```

</details>

------------------------------------------------------------------------------------------


#### Validate ANCPI Land Registry information

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/validateCarteFunciara</b></code> <code>Validates a combination of nrCf/nrCad against ANCPI electronic database</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |


##### Headers

> | Key      | Value               | description                                                           |
> |----------|---------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | judet      |  required | String   | County - From value list  |
> | uat      |  required | String   | Administrative unit - From value list  |
> | nrCf      |  required | String   | Carte Funciara  |
> | nrCad      |  required | String   | Numar Cadastru  |

###### Example
```bash
curl -L 'https://$uri/api/partners/validateCarteFunciara' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' \
-H 'Content-Type: application/json' \
-d '{
    "judet":"Dâmbovița",
    "uat":"Tartasesti",
    "nrCf":"1234-C1-U2",
    "nrCad":"1234-C1-U2"
}'
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)    |
> | `401`         | `text/html;charset=utf-8`         | None  |


##### Response Body

> | name        |   data type  | description                                       |
> |-------------|--------------|---------------------------------------------------|
> | status      |   String   | <ul><li>"OK" - combination is valid and found in ANCPI database</li><li>"WARN" - combination not found in ANCPI database</li><li>"ERROR" - error validating combination (see code)</li></ul>  |
> | code      |   String   | From value list |

###### Example
```json
{
    "status": "OK",
    "code": "VALIDATION_SUCCESS"
}
```

</details>

------------------------------------------------------------------------------------------

#### Validate ANCPI Parcel Map information

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/validatePlanCadastral</b></code> <code>Validates a combination of nrCf/nrCad against ANCPI electronic database</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |


##### Headers

> | Key      | Value               | description                                                           |
> |----------|---------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | judet      |  required | String   | County - From value list  |
> | uat      |  required | String   | Administrative unit - From value list  |
> | nrCf      |  required | String   | Carte Funciara  |
> | nrCad      |  required | String   | Numar Cadastru  |

###### Example
```bash
curl -L 'https://$uri/api/partners/validateCarteFunciara' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' \
-H 'Content-Type: application/json' \
-d '{
    "judet":"Dâmbovița",
    "uat":"Tartasesti",
    "nrCf":"1234-C1-U2",
    "nrCad":"1234-C1-U2"
}'
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)    |
> | `401`         | `text/html;charset=utf-8`         | None  |


##### Response Body

> | name        |   data type  | description                                       |
> |-------------|--------------|---------------------------------------------------|
> | status      |   String   | <ul><li>"OK" - combination is valid and found in ANCPI database</li><li>"WARN" - combination not found in ANCPI database</li><li>"ERROR" - error validating combination (see code)</li></ul>  |
> | code      |   String   | From value list |

###### Example
```json
{
    "status": "OK",
    "code": "VALIDATION_SUCCESS"
}
```

</details>

------------------------------------------------------------------------------------------

#### Create a new request

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/submitRequest</b></code> <code>(creates a new request)</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |

##### Headers

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | partnerReferenceId      |  required | String   | Partner's unique internal ID of request  |
> | priority      |  required | String   | "Low" or "High"  |
> | requestType      |  required | String   | "CARTE_FUNCIARA" or "PLAN_CADASTRAL"  |
> | judet      |  required | String   | County - From value list (Provided by OpenCode)  |
> | uat      |  required | String   | Administrative unit - From value list (Provided by OpenCode)  |
> | nrCf      |  required | String   | Carte Funciara  |
> | nrCad      |  required | String   | Numar Cadastru  |
> | nrTopo      |  optional | String   | Numar Topografic  |

###### Example
```bash
curl -L 'https://$uri/api/partners/submitRequest' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' \
-H 'Content-Type: application/json' \
-d '{
    "partnerReferenceId":"00001",
    "priority": "Low",
    "requestType": "CARTE_FUNCIARA",
    "judet":"Gorj",
    "uat":"Târgu Jiu",
    "nrCf":"1234",
    "nrCad":"567/1/14",
    "nrTopo": ""
}'
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)                             |
> | `400`         | `text/html;charset=utf-8` | None   |
> | `401`         | `text/html;charset=utf-8`         | None                                   |


##### Response Body

> | name      |   data type               | description                   |
> |-----------|-----------|-------------------------|
> | requestId      |   String   | Internal request ID  |

###### Example
```json
{
"requestId":  "jrurF1FhZ7nuyYAdy6Xm"
}
```

</details>

------------------------------------------------------------------------------------------

#### Cancel request

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/cancelRequest</b></code> <code>(cancels a request - only from Created or RetrySendToANCPI)</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |

##### Headers

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | requestId      |  required | String   | Internal request ID  |

###### Example
```bash
curl -L 'https://$uri/api/partners/cancelRequest' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' \
-H 'Content-Type: application/json' \
-d '{
    "requestId": "jrurF1FhZ7nuyYAdy6Xm"
}'
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)    |
> | `400`         | `text/html;charset=utf-8` | None   |
> | `401`         | `text/html;charset=utf-8`         | None  |
> | `404`         | `text/html;charset=utf-8`         | None  |
> | `409`         | `text/html;charset=utf-8`         | None  |


##### Response Body

> | name      |   data type               | description                   |
> |-----------|-----------|-------------------------|
> | requestId      |   String   | Internal request ID  |
> | requestStatus      |   String   | Request Status - Cancelled  |

###### Example
```json
{
"requestId":  "jrurF1FhZ7nuyYAdy6Xm",
"requestStatus": "Cancelled"
}
```

</details>

------------------------------------------------------------------------------------------

#### Query request status

<details>
 <summary><code>POST</code> <code><b>{uri}/api/partners/queryRequestStatus</b></code> <code>(query request status)</code></summary>

##### Endpoint

> | Key      | Value               | description                                                           |
> |-----------|-------------------------|-----------------------------------------------------------------------|
> | uri      | String  | Provided by OpenCode (STAGING / PROD)  |


##### Headers

> | Key      | Value               | description                                                           |
> |----------|---------------------|-----------------------------------------------------------------------|
> | Authorization      | Basic Auth   | Provided by OpenCode  |
> | X-OCD-Partner      | String   | Provided by OpenCode  |

##### Body

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | requestId      |  required | String   | Internal request ID  |

###### Example
```bash
curl -L 'https://$uri/api/partners/queryRequestStatus' \
-u '$user:$password' \
-H 'X-OCD-Partner: $partnerId' \
-H 'Content-Type: application/json' \
-d '{
    "requestId": "jrurF1FhZ7nuyYAdy6Xm"
}'
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`        | object (JSON)    |
> | `400`         | `text/html;charset=utf-8` | None   |
> | `401`         | `text/html;charset=utf-8`         | None  |
> | `404`         | `text/html;charset=utf-8`         | None  |


##### Response Body

> | name        |   data type  | description                                       |
> |-------------|--------------|---------------------------------------------------|
> | partnerReferenceId      |   String   | Partner's unique internal ID of request  |
> | requestStatus      |   String   | Request Status  |
> | ancpiOrderId | String | ANCPI Order ID |
> | docUri      |   Array [ String ]   | Direct download URIs for generated documents (present only if generated)  |

###### Example
```json
{
"partnerRef":  "d5f3af8e",
"requestStatus":  "Finalised",
"ancpiOrderId": "5950496",
"docUri":  ["https://storage.googleapis.com/download/storage/v1/b/certificatconstatator-dev.appspot.com/o/_data1_portal_ccfil_certificate_2023_3_6_certificat0000-0000Q.pdf?generation=1678138325733513&alt=media"]
}
```

</details>

------------------------------------------------------------------------------------------


#### Value Lists
<details>
 <summary>requestType</summary>
 
 ```javascript
 "CARTE_FUNCIARA"
 "PLAN_CADASTRAL"
 ```
</details>

<details>
 <summary>requestStatus</summary>
 
> | Option   |  Description                                                           |
> |----------|----------------------------------------------------------------|
> | Created      | Request received and loaded to backend systems  |
> | Cancelled | Request cancelled by partner |
> | SendingToANCPI      | In progress - API create ANCPI request |
> | RetrySendToANCPI | Postponed - API create ANCPI request |
> | SentToANCPI | Request is sent to ANCPI and waiting for document |
> | DownloadANCPI | In progress - check ANCPI for document generation |
> | RetryDownloadANCPI | Postponed - check ANCPI for document generation |
> | DoneANCPI | Document is generated and available |
> | InvoiceGeneratedANCPI | ANCPI invoice is generated and available |
> | Finalised | Request is finalised |

</details>

<details>
 <summary>Validation status "code"</summary>
 
> | Option   |  Description                                                           |
> |----------|----------------------------------------------------------------|
> | SEARCH_SUCCESS | |
> | VALIDATION_SUCCESS      |   |
> | WARN_NOT_IDENTIFIED |  |
> | WARN_VALIDATION_FAILED      |  |
> | WARN_UNKNOWN_ANCPI_RESPONSE |  |
> | ERR_INVALID_JUDET |  |
> | ERR_INVALID_UAT |  |
> | ERR_ANCPI_LOGIN_UNAVAILABLE |  |
> | ERR_ANCPI_EPAY_CONFIG_UNAVAILABLE |  |
> | ERR_ANCPI_EPAY_SEARCH_UNAVAILABLE |  |
> | ERR_ANCPI_EPAY_VALIDATE_UNAVAILABLE |  |
> | ERR_UNKNOWN_SEARCH_ERROR | |
> | ERR_UNKNOWN_VALIDATION_ERROR |  |

</details>
