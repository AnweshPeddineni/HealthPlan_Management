# Advanced Big Data Application and Indexing technologies.

# HealthPlan_Management

The Health Plan API is a RESTful API that provides CRUD operations for managing health plan-related JSON objects. It supports validation against a JSON schema, advanced semantics for operations, and data storage in a key/value store. Additionally, the API integrates RabbitMQ for messaging and ElasticSearch for powerful data indexing and querying. The API is built using Spring Boot and utilizes Redis as the underlying database.

## Additional Features

- **Patch API:** The API supports the PATCH method for partial updates to complex JSON objects, allowing modifications to nested structures.
- **Conditional Read:** Implement conditional read operations that check ETag headers to ensure data consistency before returning responses.
- **Conditional Write:** Implement conditional write operations that consider ETag headers to prevent conflicts during updates.
- **Authorization with RS256:** Use asymmetric key RS256-based JWTs for secure authentication and authorization, ensuring only authorized users access the API endpoints.


## Technologies Used

- Spring Boot: A Java framework for building robust and scalable applications.
- Redis: An in-memory data store used for storing health plan data.
- ElasticSearch: A distributed, RESTful search and analytics engine for data indexing and querying.
- RabbitMQ: A message broker that facilitates communication between different parts of an application.
- JSON Schema: A specification for defining the structure, data types, and validation rules for JSON objects.
- Postman: A popular tool for testing and interacting with APIs.

## Requirements

To run the Health Plan API locally, you need to have the following software installed:

- Java Development Kit (JDK) 17 or higher
- Redis Server
- ElasticSearch
- RabbitMQ
- Kibana

