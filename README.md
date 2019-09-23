# Syntax IQ API v1.0

The Syntax IQ API is RESTful and allows you to generate product descriptions
using HTTP requests. All responses return JSON objects, including errors.

## Authentication

The Syntax IQ API supports authentication via an API Key. You must provide
your `api_key` for every request.

You can grab your API key from your
[account](https://console.syntaxiq.com/settings).

Only one API key is active at a time. Take care to keep your API key secret!


## Base URL

To ensure data privacy, all API requests must be made over HTTPS. Unencrypted
requests made over plain HTTP are not supported.

```
https://api.syntaxiq.com/v1
```

## HTTP Status Code Summary

**200 OK** - Everything worked as expected.

**400 Bad Request** - We couldn't understand your request. Typically missing a parameter.

**401 Unauthorized** - Either no authentication credentials were provided or they are invalid.

**402 Payment Required** - Account does not have a enough credit to perform request.

**429 Too Many Requests** - You've hit the rate limit, wait a bit.

**500 Server Error** - Something unexpected happened on our end.


### Errors

When you a receive a response with a status code in the 4xx or 5xx range, you'll receive a JSON object in the body with details. The object will have a `error` and `message` key, like so:

```
{
    "error": {
        "message": "Our servers are busy right now, please try again!"
    }
}
```

### Rate Limit

Each account can only make 5 requests per second. If you need more mail us at [support@syntaxiq.com](mailto:support@syntaxiq.com).


# Usage

### Generate Description
```POST /describe```

```sh
$ curl --request POST \
  --url 'https://api.syntaxiq.com/v1/describe?api_key=$API_KEY' \
  --F 'file=@path/to/local/file'
```

```json
{
  "result": {
    "description": "Description here"
  }
}
```
