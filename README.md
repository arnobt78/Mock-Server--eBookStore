## eBookStore Mock Server

![Screenshot 2024-09-03 at 19 04 12](https://github.com/user-attachments/assets/fbfa7567-799e-4415-b37d-0a82fa96fbc7) ![Screenshot 2024-09-03 at 19 04 34](https://github.com/user-attachments/assets/a1701da8-19dc-4493-b02d-f2cb4e37feea) ![Screenshot 2024-09-03 at 19 04 50](https://github.com/user-attachments/assets/580eb690-e02b-4123-be4f-7c6b82bb4985) ![Screenshot 2024-09-03 at 19 05 04](https://github.com/user-attachments/assets/695f1bd5-3d8f-4049-9a11-f3f3a7805fda) ![Screenshot 2024-09-03 at 19 05 24](https://github.com/user-attachments/assets/25cf13dc-84c3-46f7-a9f9-9449da72123a) ![Screenshot 2024-09-03 at 19 06 17](https://github.com/user-attachments/assets/f35ea3d3-43ba-4114-8508-fb6509af8232) ![Screenshot 2024-09-03 at 19 07 19](https://github.com/user-attachments/assets/b8d5f055-7719-47d7-901c-f86b7b7f78f5) ![Screenshot 2024-09-03 at 19 07 42](https://github.com/user-attachments/assets/64583a22-c1b6-42e3-b459-d9c95002b2af) ![Screenshot 2024-09-03 at 19 07 52](https://github.com/user-attachments/assets/8772d23c-f95f-454d-957f-16d98936cf32) ![Screenshot 2024-09-03 at 19 08 45](https://github.com/user-attachments/assets/5e1a348b-f873-463d-9e8c-27e4f1e12aff) ![Screenshot 2024-09-03 at 19 09 19](https://github.com/user-attachments/assets/2dafa0c2-451a-4333-99a8-0167d9493df4) ![Screenshot 2024-09-03 at 19 09 29](https://github.com/user-attachments/assets/7a565cef-3caf-4295-b1b0-b3cc35086276) ![Screenshot 2024-09-03 at 19 09 43](https://github.com/user-attachments/assets/26854077-9177-40c6-9337-3bb3ec0ebd19) ![Screenshot 2024-09-03 at 19 10 10](https://github.com/user-attachments/assets/006d3b5b-a967-4dd6-9dee-2bf662c4d6c2)

This project sets up a mock server for the eBookStore project using `Express`, `json-server`, and `json-server-auth`. It serves mock data for products, featured products, orders, and users, and includes authentication and authorization.

Backend webpage can be seen by using this URL: https://codebook-mock-server-j8n3.onrender.com

Frontend webpage can be seen by using this URL: https://ebookstore-arnob.netlify.app

(To view the Frontend Source Folder, Visit: https://ebookstore-arnob.netlify.app/ )



## Project Structure

```
.gitignore
data/
    db.json
    routes.json
index.js
package.json
```

- .gitignore: Specifies files and directories to be ignored by Git.
- data: Contains JSON files for mock data.
  - db.json: Contains mock data for products, featured products, orders, and users.
  - routes.json: Defines custom routes for the mock server.
- index.js: Main entry point for the server.
- package.json: Contains project metadata and dependencies.

## Prerequisites

- Node.js installed on your machine.
- npm (Node Package Manager) installed.

## Installation

1. Clone the repository:

```sh
git clone <repository-url>
cd codebook-mock-server
```

2. Install dependencies:

```sh
npm install
```

## Running the Server

To start the server, run:

```sh
npm start
```

This will start the server on `http://localhost:8000`.

## Server Configuration

### index.js

The main server configuration is done in the index.js file. Here is a breakdown of what each part does:

1. **Import Dependencies**:
    ```javascript
    import express from "express";
    import jsonServer from "json-server";
    import auth from "json-server-auth";
    ```

2. **Initialize Express Server**:
    ```javascript
    const server = express();
    ```

3. **Set CORS Headers**:
    ```javascript
    server.use((req, res, next) => {
        res.header('Access-Control-Allow-Origin', '*');
        res.header('Access-Control-Allow-Headers', '*');
        next();
    });
    ```

4. **Setup JSON Server Router**:
    ```javascript
    const router = jsonServer.router('./data/db.json');
    server.use('/api', router);
    server.db = router.db;
    ```

5. **Setup Middlewares**:
    ```javascript
    const middlewares = jsonServer.defaults();
    ```

6. **Setup Authentication Rules**:
    ```javascript
    const rules = auth.rewriter({
        products: 444,
        featured_products: 444,
        orders: 660,
        users: 600
    });
    ```

7. **Use Authentication and Middlewares**:
    ```javascript
    server.use(rules);
    server.use(auth);
    server.use(middlewares);
    server.use(router);
    ```

8. **Start the Server**:
    ```javascript
    server.listen(8000);
    ```

### db.json

Contains mock data for the server. The structure includes:

- `products`: List of products.
- `featured_products`: List of featured products.
- `orders`: List of orders.
- `users`: List of users.

### routes.json

Defines custom routes for the server. Example:

```json
{
    "/products*": "/444/",
    "/featured_products*": "/444/",
    "/orders*": "/660/",
    "/users*": "/600/"
}
```

## API Endpoints

The server provides the following endpoints:

- `GET /api/products`: Fetch all products.
- `GET /api/featured_products`: Fetch all featured products.
- `GET /api/orders`: Fetch all orders.
- `GET /api/users`: Fetch all users.

## Authentication

The server uses `json-server-auth` for authentication. The rules are defined in the index.js file:

```javascript
const rules = auth.rewriter({
    products: 444,
    featured_products: 444,
    orders: 660,
    users: 600
});
```

- `444`: Read-only access.
- `660`: Read and write access.
- `600`: Full access.
