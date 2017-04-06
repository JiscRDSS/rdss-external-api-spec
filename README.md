# rdss-external-api-spec

## Introduction

This API will follow the (current HTTP RFC)[https://tools.ietf.org/html/rfc7231].


## RESTful external API specification

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

### Comformance

The keywords **MAY**, **MUST**, **MUST NOT**, **NOT RECOMMENDED**, **RECOMMENDED**, **SHOULD** and **SHOULD NOT** are to be interpreted as described in [RFC2219](https://tools.ietf.org/html/rfc2119).

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
Content-Length: 5
Cache-Control: max-age=0, private
```

All timestamps are returned in ISO 8601 format:

``` 
YYYY-MM-DDTHH:MM:SSZ 
```

### Rate limiting

The rate limit allows you to make up to 100 requests per hour.

You can check the returned HTTP headers of any API request to see your current rate limit status

```
HTTP/1.1 200 OK
Date: Mon, 01 Jul 2013 17:27:06 GMT
Status: 200 OK
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 56
X-RateLimit-Reset: 1372700873

```
| Header Name    | Description                                                                                 |
|----------------|---------------------------------------------------------------------------------------------|
| `X-RateLimit-Limit` | The maximum number of requests that the consumer is permitted to make per hour.        |
| `X-RateLimit-Remaining` | The number of requests remaining in the current rate limit window.                 |
| `X-RateLimit-Reset` | The time at which the current rate limit window resets in UTC [epoch seconds]    (https://en.wikipedia.org/wiki/Unix_time).                                                                     |

Once you go over the rate limit you will receive an error response:

```
HTTP/1.1 403 Forbidden
Date: Tue, 20 Aug 2013 14:50:41 GMT
Status: 403 Forbidden
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1377013266
{
    "message": "API rate limit exceeded for xxx.xxx.xxx.xxx."
    "documentation_url" : "https://github.com/JiscRDSS/rdss-external-api-spec"
}

```

### Cross Origin Resource Sharing

The API supports Cross Origin Resource Sharing (CORS) for AJAX requests from any origin. You can read the [CORS W3C Recommendation](https://www.w3.org/TR/cors/), or [this intro](https://code.google.com/archive/p/html5security/wikis/CrossOriginRequestSecurity.wiki) from the HTML 5 Security Guide.

Here's a sample request sent from a browser hitting http://example.com:

```
curl -i https://www.jisc.ac.uk -H "Origin: http://example.com"
HTTP/1.1 302 Found
Access-Control-Allow-Origin: *
Access-Control-Expose-Headers: X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset

```

### Pagination 

Requests that return multiple items will be paginated to 30 items by default.

(To be continued)
