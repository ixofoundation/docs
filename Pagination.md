---
stoplight-id: 8xgri9vqv63qo
---

# Pagination in IXO Blocksync GraphQL API

Pagination is crucial for managing large datasets efficiently, ensuring smooth navigation and data retrieval without overwhelming clients or servers. This section outlines the pagination methods and best practices employed by the IXO Blocksync GraphQL API to assist developers in handling extensive data collections effectively.

## Overview of Pagination in IXO Blocksync GraphQL API

The IXO Blocksync GraphQL API always uses 10 items as the default pagination value across all queries.

The IXO Blocksync GraphQL API leverages cursor-based pagination to enable efficient data retrieval. This approach is highly effective for situations where data may change frequently, as it uses a reference to a specific point in the dataset to fetch the next set of results. Cursor-based pagination ensures better performance and consistency compared to traditional offset-based pagination.

## Pagination Parameters in GraphQL

The IXO Blocksync GraphQL API also supports the `last` and `before` parameters for pagination, in addition to `first` and `after`.

The IXO Blocksync GraphQL API supports the following key arguments to manage pagination efficiently:

### 1. **first**
- **Description**: Defines the number of records to return in each query.
- **Default Value**: If not specified, a default value is applied, always 10 items per request.
- **Usage**: Use this parameter to control the number of items returned per query. Example:
  ```graphql
  query {
    entities(first: 50) {
      edges {
        node {
          id
          name
        }
      }
    }
  }
  ```
  This request returns up to 50 entities.

### 2. **last**
- **Description**: Defines the number of records to return, but starting from the end of the dataset. This is useful for navigating backward through results.
- **Usage**: Use this parameter to get the last N items from a dataset.
  ```graphql
  query {
    entities(last: 10) {
      edges {
        node {
          id
          name
        }
      }
    }
  }
  ```
  This request returns the last 10 entities.

### 3. **after**
- **Description**: The `after` parameter is used as a cursor to indicate the point in the dataset from which to continue fetching results. It allows you to fetch subsequent pages without redundancy.
- **Usage**: To retrieve the next set of results, include the `after` value returned in the previous response:
  ```graphql
  query {
    entities(first: 20, after: "YXJyYXljb25uZWN0aW9uOjEw") {
      edges {
        node {
          id
          name
        }
      }
    }
  }
  ```
  This query will fetch the next set of entities starting from the provided cursor.

### 4. **before**
- **Description**: The `before` parameter is used to navigate backward from a specific point in the dataset.
- **Usage**: To retrieve previous results, include the `before` value from the previous response:
  ```graphql
  query {
    entities(last: 10, before: "YXJyYXljb25uZWN0aW9uOjIw") {
      edges {
        node {
          id
          name
        }
      }
    }
  }
  ```
  This request fetches entities that appear before the given cursor.

## Example Pagination Response

A response from the GraphQL API includes pagination metadata that helps in navigating through the dataset.

### Example Response:
```json
{
  "data": {
    "entities": {
      "edges": [
        {
          "node": {
            "id": "did:ixo:entity:001",
            "name": "Entity One"
          }
        },
        {
          "node": {
            "id": "did:ixo:entity:002",
            "name": "Entity Two"
          }
        }
      ],
      "pageInfo": {
        "endCursor": "YXJyYXljb25uZWN0aW9uOjIw",
        "hasNextPage": true
      }
    }
  }
}
```

- **edges**: Contains the array of results returned for the current request.
- **pageInfo.endCursor**: Represents the reference point for the next set of results.
- **pageInfo.hasNextPage**: Indicates whether more data is available to be fetched.

## Best Practices for Using Pagination in GraphQL

### 1. **Specify Reasonable Limits**
When specifying the `first` argument, select a value that strikes a balance between performance and usability. Setting a large value may slow down responses and increase resource consumption, whereas a very small value could lead to excessive API calls. Generally, 20 to 100 items per query is a good range.

### 2. **Handle End of Data Gracefully**
Be prepared to handle scenarios where no further data is available. If `pageInfo.hasNextPage` is `false`, it indicates that there are no more pages to retrieve.

### 3. **Avoid Hardcoding Cursors**
Cursors are typically encoded and can vary based on the state of the dataset. Avoid hardcoding cursor values, and instead rely on the `endCursor` value provided in each response to continue pagination.

### 4. **Monitor Rate Limits**
When paginating through large datasets, ensure your client respects the rate limits set by the IXO Blocksync GraphQL API to prevent receiving `429 Too Many Requests` errors. If rate limits are exceeded, consider implementing retry logic with exponential backoff.

## Error Handling for Pagination

Errors may occur during pagination, particularly when dealing with extensive datasets or if a cursor becomes invalid due to changes in the data. Here are some common errors to handle:

- **400 Bad Request**: This error may arise if an invalid cursor is provided. Always use the cursor as returned in the previous response.
- **429 Too Many Requests**: Ensure that you do not exceed the allowed rate limits while paginating. Implement retry logic if rate limits are reached.

