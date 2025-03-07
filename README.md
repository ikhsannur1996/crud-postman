## Setting Up Postman for CRUD Operations

### Prerequisites
- **Postman Installed**: Ensure you have Postman installed on your machine.
- **API Endpoint**: Have a running API server, such as JSON Server with a `db.json` file.

### Step-by-Step Guide

#### 1. Create a New Request in Postman
- Open Postman.
- Click on the **"New"** button or the **"+"** tab to create a new request.
- Select **"HTTP Request"**.

#### 2. Read Operation (GET)
To retrieve resources:

- **Method**: Select **GET**.
- **URL**: Enter your endpoint URL to fetch all posts, e.g., `http://localhost:3000/posts`.
- Click on **Send**. You will get a response with the list of posts (HTTP status code 200).

To fetch a single resource:
- Change the URL to `http://localhost:3000/posts/1` (replace `1` with the desired post ID).
- Click on **Send** to see the specific post details.

#### 3. Create Operation (POST)
To create a new resource:

- **Method**: Select **POST**.
- **URL**: Enter your endpoint URL, e.g., `http://localhost:3000/posts`.
- **Body**: Select the **Body** tab, choose **raw**, and set the type to **JSON**. Enter your JSON data:

```json
{
  "id": "1",
  "name": "John Doe",
  "age": 20,
  "gender": "Male",
  "hobby": "Photography",
  "city": "Jakarta",
  "dream": "To become a professional photographer"
}
```

- Click on **Send**. You should receive a response indicating success (e.g., HTTP status code 201).

#### 4. Update Operation (PUT)
To update an existing resource completely:

- **Method**: Select **PUT**.
- **URL**: Enter your endpoint URL for the specific resource, e.g., `http://localhost:3000/posts/1`.
- **Body**: Choose raw and set it to JSON format. Enter updated data:

```json
{
  "id": "1",
  "name": "John Doe",
  "age": 20,
  "gender": "Male",
  "hobby": "Photography",
  "city": "Semarang",
  "dream": "To become a professional photographer"
}
```

- Click on **Send**. You should receive a response indicating success (HTTP status code 200).

#### 5. Partial Update Operation (PATCH)
To partially update an existing resource:

- **Method**: Select **PATCH**.
- **URL**: Enter your endpoint URL for the specific resource, e.g., `http://localhost:3000/posts/1`.
- **Body**: Choose raw and set it to JSON format. Enter only the fields you want to update:

```json
{
  "city": "Bandung"
}
```

This request updates only the `views` field of the post with ID `1`.

- Click on **Send**. You should receive a response indicating success (HTTP status code 200).

#### 6. Delete Operation (DELETE)
To delete a resource:

- **Method**: Select **DELETE**.
- **URL**: Enter your endpoint URL for the specific resource, e.g., `http://localhost:3000/posts/1`.
- Click on **Send**. You should receive a response indicating success (HTTP status code 204).

### Custom Response Testing in Postman

When performing CRUD operations, it's essential to validate the responses received from your API. Here’s how you can create tests in Postman for various scenarios:

#### Check for Successful Response

You can verify that your API responds correctly by checking for expected status codes.

```javascript
// Check for successful response
pm.test("Response status is 200 OK", function () {
    pm.response.to.have.status(200);
});
```

#### Check for Error Responses

Customize this based on expected errors.

```javascript
// Check for error response (you can customize this based on expected errors)
pm.test("Response status is 400 or 500", function () {
    pm.response.to.have.status(400).or.to.have.status(500);
});
```

#### Check if Resource is Created Successfully

When creating a new resource, ensure that you receive a status of 201 Created.

```javascript
// Check if the response status is 201 Created
pm.test("Response status is 201 Created", function () {
    pm.response.to.have.status(201);
});
```

### Conclusion
By following these steps, you can effectively perform CRUD operations using Postman and validate responses through custom tests. This setup not only aids in testing but also enhances development efficiency by ensuring that your API behaves as expected.

For further reading and examples, refer to:
- [Postman CRUD Operations Guide](https://blog.nashtechglobal.com/postman-crud/) 
- [MDN Web Docs on PATCH](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PATCH)
