# ALX Project 0x14 - MoviesDatabase API

## Introduction
This project is aimed at understanding and working with APIs effectively, particularly focusing on using the MoviesDatabase API. By studying the API documentation, we learn how to make requests, handle responses, and utilize TypeScript to create clear and robust type definitions for both requests and responses. The ultimate goal is to demonstrate proficiency in interacting with APIs and managing their data in a structured manner.

## API Overview
The MoviesDatabase API provides a powerful interface for accessing data related to movies, TV shows, and celebrities. It supports various features such as:
- Searching for movies and TV shows by title or keyword.
- Fetching detailed information about specific movies or TV shows, including cast, crew, and release dates.
- Retrieving trending movies or TV shows based on user activity.
- Accessing celebrity profiles and their filmography.

This API is designed to support developers in building applications that require access to comprehensive and up-to-date entertainment data.

## Version
API Version: v1

## Available Endpoints
### 1. **Search for Movies**
- **Endpoint**: `/movies/search`
- **Method**: `GET`
- **Description**: Retrieves a list of movies that match the specified search query.
- **Query Parameters**:
  - `query` (string, required): The search term to find matching movies.
  - `year` (number, optional): Filter results by release year.
  
### 2. **Get Movie Details**
- **Endpoint**: `/movies/{id}`
- **Method**: `GET`
- **Description**: Retrieves detailed information about a specific movie using its unique ID.
- **Path Parameters**:
  - `id` (string, required): The unique identifier of the movie.

### 3. **Trending Movies and Shows**
- **Endpoint**: `/trending`
- **Method**: `GET`
- **Description**: Fetches a list of movies or TV shows that are currently trending.
- **Query Parameters**:
  - `type` (string, optional): Specifies the type of content (`movie` or `tv`).

### 4. **Get Celebrity Details**
- **Endpoint**: `/celebrities/{id}`
- **Method**: `GET`
- **Description**: Retrieves detailed information about a celebrity, including their biography and filmography.
- **Path Parameters**:
  - `id` (string, required): The unique identifier of the celebrity.

## Request and Response Format

### Request Example
**Endpoint**: `/movies/search`
**Method**: `GET`
**Headers**:
```json
{
  "Authorization": "Bearer your_api_key"
}
```
**Query Parameters**:
```json
{
  "query": "Inception",
  "year": 2010
}
```

### Response Example
**Successful Response**:
```json
{
  "data": [
    {
      "id": "1a2b3c",
      "title": "Inception",
      "year": 2010,
      "genre": ["Action", "Sci-Fi"],
      "director": "Christopher Nolan",
      "cast": ["Leonardo DiCaprio", "Joseph Gordon-Levitt"]
    }
  ],
  "status": "success"
}
```

**Error Response**:
```json
{
  "status": "error",
  "message": "Invalid API key",
  "code": 401
}
```

## Authentication
The MoviesDatabase API requires authentication for most of its endpoints. Authentication is managed through an API key, which must be included in the request either as a query parameter or in the request headers.

### Authentication Methods
1. **Query Parameter**:
   - Add `?api_key=your_api_key` to the URL.
   
2. **Request Headers**:
   - Include the following header:
     ```
     Authorization: Bearer your_api_key
     ```

## Error Handling
### Common Errors
- **401 Unauthorized**: Indicates that the API key is missing or invalid.
- **404 Not Found**: The requested resource does not exist.
- **429 Too Many Requests**: The user has exceeded the rate limit.

### Best Practices for Handling Errors
- Check the response status code and log detailed error messages for debugging.
- Implement retries with exponential backoff for `429 Too Many Requests` errors.
- Inform users with clear error messages when requests fail.

## Usage Limits and Best Practices
### Rate Limits
- The API allows a maximum of **100 requests per minute**.
- Exceeding this limit will result in a `429 Too Many Requests` error.

### Best Practices
- **Caching**: Cache frequently accessed data to reduce API calls and improve performance.
- **Efficient Queries**: Use specific search terms and filters to minimize unnecessary data retrieval.
- **Secure Storage**: Store your API key securely using environment variables or secure vaults.
- **Monitoring**: Track the number of API calls and ensure compliance with rate limits.

## Conclusion
This project provides a practical approach to working with APIs, focusing on leveraging TypeScript to define and manage data structures effectively. By understanding the MoviesDatabase API's features and limitations, we can build robust applications that utilize its entertainment data efficiently.
