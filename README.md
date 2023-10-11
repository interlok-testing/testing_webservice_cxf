## Webservice CXF Testing

[![license](https://img.shields.io/github/license/interlok-testing/testing_webservice_cxf.svg)](https://github.com/interlok-testing/testing_webservice_cxf/blob/develop/LICENSE)
[![Actions Status](https://github.com/interlok-testing/testing_webservice_cxf/actions/workflows/gradle-build.yml/badge.svg)](https://github.com/interlok-testing/testing_webservice_cxf/actions/workflows/gradle-build.yml)

Project tests interlok-webservice-cxf and interlok-json features

## What it does

This project has a single workflow that implements a simple HTTP json API that calls two SOAP services, parses the result data and returns it as a json HTTP response.

![Webservice CXF Diagram](/webservice-cxf-diagram.png "Webservice CXF Diagram")

The two SOAP services used are:

* InvertStringCase in https://www.dataaccess.com/webservicesserver/TextCasing.wso: Uppercase letters that are lowercase and lowercase letters that are uppercase.
* NumberToWords in https://www.dataaccess.com/webservicesserver/NumberConversion.wso: Returns the word corresponding to the positive number passed as parameter. Limited to quadrillions.

## Getting started

* `./gradlew clean build`
* `(cd ./build/distribution && java -jar lib/interlok-boot.jar)`

The API is available at `http://localhost:8080/api/webservice-proxy`

## Try it

You can call the api with the following curl commands:

### Call the API

`curl --location --request POST 'http://localhost:8080/api/webservice-proxy' --header 'Content-Type: application/json' --data-raw '{ "NumberToWords":"123", "InvertCase":"hellow world" }'`

And you can expect a response like:

```json
{
    "ResultInvertCase": "HELLOW WORLD",
    "ResultNumberToWords": "one hundred and twenty three "
}
```
