# Customer Process Validator API

## Purpose
This project was created as part of the tech hunting code challenge for the position of mulesoft developer.

## Requirements

The current project was developed using:

* Mulesoft 4.12.0 EE
* Anypoint Studio 7.26.0
* Raml 1.0
* OpenAPI 3.0

## Development Considerations

This API was created as intended for a process API in the API Led connectivity architechture.

The API uses RAML as main descriptor of the service since it is the mule recommended main language used for the C4E across organizations.

The RAML files were created locally and the ApiKit router and console were scaffolded from the RAML definition.

The Architecture inside the project can be found in this repository, it is worth to look at the resource oriented architecture as intended for REST services.

The Error handling strategy defined for this project is the global error handler since there were no specific error considerations for this development.

## Documents:

### OpenAPI

Here you can find the OpenAPI documentation for this service: [customerApi.json](/src/resources/customersApi.json)

### DataWeave Script

Here you can check the Dataweave Script used to complete this challenge: [customersTransformation.dw](/src/resources/customersTransformation.dw)

#### Execution in Playground

If you want to execute the script in the dataweave playgroud, you will need to change the mimeType validation created to identify the source of the customer if internal or external.

The mimeType validation was created as per it is more robust when validating the payloads.

Replace the next code:
```
var src = if (payload.^mimeType == "application/json") payload
else if (payload.^mimeType == "application/xml") payload.Customer
else null
```

with:
```
var src = if (payload.Customer != null) payload.Customer else payload
```

### Console

This section is created to demonstrate the built in console created for this project using the RAML files.

To access the consolde, run the service in the Anypoint Studio and access the url: http://localhost:8081/console/

![Console Login](/src/resources/images/console1.png)
![Console Main Page](/src/resources/images/console2.png)
![Console Body Examples Json](/src/resources/images/console3.png)
![Console Body Examples Xml](/src/resources/images/console4.png)
![Console Successful Responses](/src/resources/images/console5.png)
![Console Failed Responses](/src/resources/images/console6.png)


