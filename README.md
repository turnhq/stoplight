### Stoplight
`TurnAPIStoplight.yml` is our public API using [The OpenAPI Specification v3.0](https://swagger.io/blog/news/whats-new-in-openapi-3-0/).

The other two files, are our legacy Postman collection, and were used to generate the initial OpenAPI YAML file using [Apimatic](https://www.apimatic.io/dashboard?modal=transform):
- `TurnAPI.postman_collection.json`
- `TurnAPI.postman_globals.json`

It is connected to our Stoplight account, we can make changes to our specification by cloning this repository or making changes directly on Stoplight using their editor and the changes will be committed to this repository after saving them.
