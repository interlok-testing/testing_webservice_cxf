## Webservice CXF Testing

Project tests interlok-webservice-cxf and interlok-json features

## What it does

This project has a single workflow that implements a simple HTTP json API that calls two SOAP services, parses the result data and returns it as a json HTTP response.

![Webservice CXF Diagram](/webservice-cxf-diagram.png "Webservice CXF Diagram")

## Getting started

* `./gradlew clean build`
* `(cd ./build/distribution && java -jar lib/interlok-boot.jar)`

The API is available at `http://localhost:8080/api/webservice-proxy`

## Try it

You can call the api with the following curl commands:

### Call the API

`curl --location --request POST 'http://localhost:8080/api/webservice-proxy' \
--header 'Content-Type: application/json' \
--data-raw '{
    "NumberToWords":"123",
    "InvertCase":"hellow world"
}'`

And you can expect a response like:

```json
{
    "result_invert_case": "HELLOW WORLD",
    "result_number_to_words": "one hundred and twenty three "
}
```
