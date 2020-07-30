Introduction
----

This repository contains the current documentation for the Blinkhash Mining Pools's backend REST API (v1). The API itself is relatively simple. Each of its endpoints were designed to be self-explanatory while still providing users with standardized JSON-formatted responses, making it easy to search, filter and use our data. The base URL for all requests is https://www.blinkhash.com/api/v1. The complete URL varies depending on the endpoint of the resource being accessed. For instance, you can view the statistics for each of our supported pools via a GET request to this URL: https://www.blinkhash.com/api/v1/statistics.

Need Support?
----

If you need help with an API-related matter, the first place to look is our Discord channel, where the developers are available to answer any questions.

Documentation
----

Each of the following endpoints follow a simple structure, to promote ease of use. The status codes and JSON-formatted responses are standardized throughout. Regarding authentication, we've decided not to include any, in order to retain transparency and help our users remain anonymous. The endpoints themselves are also cached for two minutes, and consist of the following:

```
{
    endpoint: "example",
    errors: "",
    data: [Object],
}
```

The *endpoint* field indicates the current endpoint, while the *errors* field highlights any errors that may have arisen during the request. The *data* field, on the other hand, contains the user's requested data.
