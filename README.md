# rdss-external-api-spec

## RESTful external API specification

### Introduction

This repository documents the RDSS external API for organisation querying. It describes the API requirements and follows the [current HTTP RFC](https://tools.ietf.org/html/rfc7231) and Level 2 of [Richardson Maturity Model](https://martinfowler.com/articles/richardsonMaturityModel.html).

In order to see the interactive browser RAML viewer, please do one of the following:

View locally:

```
clone the repository

git clone git@github.com:JiscRDSS/rdss-external-api-spec.git

then open api.html in the browser
```

View with [github.io html preview](https://htmlpreview.github.io/)

```
Add your Github token to the following URL

https://htmlpreview.github.io/?https://raw.githubusercontent.com/JiscRDSS/rdss-external-api-spec/master/api.html?token=[your github token]

Or open the HTML in Raw view and paste htmlpreview.github.io/? after https://

```

When updating the RAML file, please re-generate the html by following the [raml2html](https://www.npmjs.com/package/raml2html) guide.

### Audience

The RDSS External API is intended for the following audience:

- Engineering
- Operations
- Quality Assurance


### Versioning

Current version:&nbsp;&nbsp;&nbsp;&nbsp;`0.0.1-SNAPSHOT`

Versioning for the RDSS external API spec follows [Semantic Versioning 2.0.0](http://semver.org/spec/v2.0.0.html).

### Conformance

The keywords **MAY**, **MUST**, **MUST NOT**, **NOT RECOMMENDED**, **RECOMMENDED**, **SHOULD** and **SHOULD NOT** are to be interpreted as described in [RFC2219](https://tools.ietf.org/html/rfc2119).

### Topology

The API functions will be stored in AWS Lambda and Web clients will call them via the Amazon API Gateway.

 <p align="center">
  <img src="topology/apigatewaysample1.png"/>
 </p>

### Schema

All API access is over HTTPS, and accessed from the https://www.jisc.ac.uk. All data is sent and received as JSON

```
curl -i https://www.jisc.ac.uk/organisation
HTTP/1.1 200 OK
Server:
Date: Mon, 03 Aug 2015 17:45:57 GMT
Content-Type: application/json; charset=utf-8
Connection: keep-alive
Status: 200 OK
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 83
X-RateLimit-Reset: 1350085394
Cache-Control: max-age=0, private
```

All timestamps are returned in ISO 8601 format:

```
YYYY-MM-DDTHH:MM:SSZ
```

Please refer to the [api.raml](api.raml) for specification and examples on:

- Caching
- Rate Limiting
- Cross Origin Resource Sharing
