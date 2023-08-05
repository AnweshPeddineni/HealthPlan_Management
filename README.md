# Advanced Big Data Application and Indexing technologies.

# HealthPlan_Management

The Health Plan API is a RESTful API that provides CRUD operations for managing health plan-related JSON objects. It supports validation against a JSON schema, advanced semantics for operations, and data storage in a key/value store. Additionally, the API integrates RabbitMQ for messaging and ElasticSearch for powerful data indexing and querying. The API is built using Spring Boot and utilizes Redis as the underlying database.

## Additional Features

- **Patch API:** The API supports the PATCH method for partial updates to complex JSON objects, allowing modifications to nested structures.
- **Conditional Read:** Implement conditional read operations that check ETag headers to ensure data consistency before returning responses.
- **Conditional Write:** Implement conditional write operations that consider ETag headers to prevent conflicts during updates.
- **Authorization with RS256:** Use asymmetric key RS256-based JWTs for secure authentication and authorization, ensuring only authorized users access the API endpoints.


### Data Flow
1. Generate token using the `/token` endpoint
2. Validate further API requests using the Bearer Token
3. Create JSON Object using the `POST` HTTP method
4. Validate incoming JSON Object using the respective JSON Schema
5. De-Structure hierarchial JSON Object while storing in Redis key-value store
6. Enqueue object in RabbitMQ queue to index the object
7. Dequeue from RabbitMQ queue and index data in ElasticServer
8. Implement Search queries using Kibana Console to retrieve indexed data

### Steps to run:
1. Install the Prerequisites for the project:
    - Redis Server (https://redis.io/download)
    - ElasticSearch (https://www.elastic.co/downloads/elasticsearch)
    - Kibana (https://www.elastic.co/downloads/kibana)
    - RabbitMQ Server (https://www.rabbitmq.com/download.html)
2. Start the Redis Server with the `redis-server` command
3. Start the ElasticSearch server with the `elasticsearch` command
4. Start Kibana with the `kibana` command
5. Start RabbitMQ server with the `rabbitmq-server` command

This would start the server. Create the data using the REST API endpoints and
query the indexed data on Kibana Console.


### API Endpoints

- GET `/token` - This generates a RSA-signed JWT token used to authenticate future requests.
- POST `/plan` - Creates a new plan provided in the request body
- PUT `/plan/{id}` - Updates an existing plan provided by the id
    - A valid Etag for the object should also be provided in the `If-Match` HTTP Request Header
- PATCH `/plan/{id}` - Patches an existing plan provided by the id
    - A valid Etag for the object should also be provided in the `If-Match` HTTP Request Header
- GET `/plan/{id}` - Fetches an existing plan provided by the id
    - An Etag for the object can be provided in the `If-None-Match` HTTP Request Header
    - If the request is successful, a valid Etag for the object is returned in the `ETag` HTTP Response Header
- DELETE `/plan/{id}` - Deletes an existing plan provided by the id
    - A valid Etag for the object should also be provided in the `If-Match` HTTP Request Header

