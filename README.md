# eBookStore Mock Server

![Screenshot 2024-09-03 at 19 04 12](https://github.com/user-attachments/assets/fbfa7567-799e-4415-b37d-0a82fa96fbc7) ![Screenshot 2024-09-03 at 19 04 34](https://github.com/user-attachments/assets/a1701da8-19dc-4493-b02d-f2cb4e37feea) ![Screenshot 2024-09-03 at 19 04 50](https://github.com/user-attachments/assets/580eb690-e02b-4123-be4f-7c6b82bb4985) ![Screenshot 2024-09-03 at 19 05 04](https://github.com/user-attachments/assets/695f1bd5-3d8f-4049-9a11-f3f3a7805fda) ![Screenshot 2024-09-03 at 19 05 24](https://github.com/user-attachments/assets/25cf13dc-84c3-46f7-a9f9-9449da72123a) ![Screenshot 2024-09-03 at 19 06 17](https://github.com/user-attachments/assets/f35ea3d3-43ba-4114-8508-fb6509af8232) ![Screenshot 2024-09-03 at 19 07 19](https://github.com/user-attachments/assets/b8d5f055-7719-47d7-901c-f86b7b7f78f5) ![Screenshot 2024-09-03 at 19 07 42](https://github.com/user-attachments/assets/64583a22-c1b6-42e3-b459-d9c95002b2af) ![Screenshot 2024-09-03 at 19 07 52](https://github.com/user-attachments/assets/8772d23c-f95f-454d-957f-16d98936cf32) ![Screenshot 2024-09-03 at 19 08 45](https://github.com/user-attachments/assets/5e1a348b-f873-463d-9e8c-27e4f1e12aff) ![Screenshot 2024-09-03 at 19 09 19](https://github.com/user-attachments/assets/2dafa0c2-451a-4333-99a8-0167d9493df4) ![Screenshot 2024-09-03 at 19 09 29](https://github.com/user-attachments/assets/7a565cef-3caf-4295-b1b0-b3cc35086276) ![Screenshot 2024-09-03 at 19 09 43](https://github.com/user-attachments/assets/26854077-9177-40c6-9337-3bb3ec0ebd19) ![Screenshot 2024-09-03 at 19 10 10](https://github.com/user-attachments/assets/006d3b5b-a967-4dd6-9dee-2bf662c4d6c2)

---

## Project Summary

The **eBookStore Mock Server** is a backend mock API server built with **Express**, **json-server**, and **json-server-auth** to simulate the eBookStore application’s backend. It provides a fully functional REST API for products, featured products, orders, and users, complete with authentication and custom access rules. This project is ideal for frontend/backend developers and learners who wish to understand API mockups, authentication, and rapid prototyping.

- **Backend Demo:** [https://codebook-mock-server-j8n3.onrender.com](https://codebook-mock-server-j8n3.onrender.com)
- **Frontend Demo:** [https://ebookstore-arnob.netlify.app](https://ebookstore-arnob.netlify.app)
- **Frontend Source:** [https://github.com/arnobt78/eBookStore--ReactJS](https://github.com/arnobt78/eBookStore--ReactJS)

---

## Table of Contents

1. [Project Structure](#project-structure)
2. [Features](#features)
3. [Technology Stack](#technology-stack)
4. [Installation](#installation)
5. [How to Run](#how-to-run)
6. [API Endpoints](#api-endpoints)
7. [Authentication & Access](#authentication--access)
8. [Example Data & Scripts](#example-data--scripts)
9. [Learning & Teaching Notes](#learning--teaching-notes)
10. [Conclusion](#conclusion)

---

## Project Structure

```
.
├── .gitignore
├── data/
│   ├── db.json
│   └── routes.json
├── index.js
├── package.json
```

- **.gitignore**: Specifies files/folders to ignore in Git.
- **data/db.json**: Stores mock data for products, featured products, orders, and users.
- **data/routes.json**: Custom route rules for the API.
- **index.js**: Main entry point; configures and starts the Express server, JSON server, and authentication.
- **package.json**: Project metadata, dependencies, and scripts.

View the project files directly for more details:  
- [db.json](https://github.com/arnobt78/Mock-Server--eBookStore/blob/main/data/db.json)  
- [routes.json](https://github.com/arnobt78/Mock-Server--eBookStore/blob/main/data/routes.json)  
- [index.js](https://github.com/arnobt78/Mock-Server--eBookStore/blob/main/index.js)  
- [package.json](https://github.com/arnobt78/Mock-Server--eBookStore/blob/main/package.json)

---

## Features

- **Full REST API** for eBookStore entities (products, featured_products, orders, users)
- **Authentication & Authorization** using `json-server-auth` (configurable access levels)
- **Custom Routing** via `routes.json`
- **CORS** enabled for easy frontend integration
- **Mock Data** for learning, prototyping, and frontend development
- **Easy Extensibility** for new resources or routes

---

## Technology Stack

- **Node.js**: Server runtime
- **Express**: Core server framework
- **json-server**: Rapid REST API mock server
- **json-server-auth**: Simple authentication/authorization layer for `json-server`

---

## Installation

### Prerequisites

- Node.js installed ([Download Node.js](https://nodejs.org/))
- npm (Node Package Manager)

### Steps

1. **Clone the Repository:**

   ```sh
   git clone <repository-url>
   cd Mock-Server--eBookStore
   ```

2. **Install Dependencies:**

   ```sh
   npm install
   ```

---

## How to Run

Start the server with:

```sh
npm start
```

- By default, the server runs on: [http://localhost:8000](http://localhost:8000)

---

## API Endpoints

All endpoints are prefixed with `/api`:

- `GET /api/products` — Fetch all products
- `GET /api/featured_products` — Fetch all featured products
- `GET /api/orders` — Fetch all orders
- `GET /api/users` — Fetch all users

**Custom routes** and access rules are defined in [`data/routes.json`](https://github.com/arnobt78/Mock-Server--eBookStore/blob/main/data/routes.json):

```json
{
    "/products*": "/444/",
    "/featured_products*": "/444/",
    "/orders*": "/660/",
    "/users*": "/600/"
}
```

---

## Authentication & Access

Authentication is handled via `json-server-auth` and rules are set in `index.js`:

```javascript
const rules = auth.rewriter({
    products: 444,           // Read-only
    featured_products: 444,  // Read-only
    orders: 660,             // Read & Write
    users: 600               // Full access
});
```

- `444` = Read-only access
- `660` = Read and write access
- `600` = Full access (CRUD)

**Authentication Example:**  
To access protected routes, you must register/login and use the provided token.

---

## Example Data & Scripts

### Example Product (`db.json`)

```json
{
  "products": [
    {
      "id": 10001,
      "name": "Basics To Advanced In React",
      "overview": "Lorem ipsum dolor sit amet consectetur adipisicing elit. Error unde quisquam magni vel eligendi nam.",
      "long_description": "Lorem ipsum dolor sit amet consectetur, adipisicing elit. Soluta aut, vel ipsum maxime quam quia, quaerat tempore minus odio exercitationem illum et eos, quas ipsa aperiam magnam officiis libero expedita quo voluptas deleniti sit dolore? Praesentium tempora cumque facere consectetur quia, molestiae quam, accusamus eius corrupti laudantium aliquid! Tempore laudantium unde labore voluptates repellat, dignissimos aperiam ad ipsum laborum recusandae voluptatem non dolore. Reiciendis cum quo illum. Dolorem, molestiae corporis.",
      "price": 29,
      "poster": "https://images.unsplash.com/photo-1633356122544-f134324a6cee?ixlib=rb-1.2.1&auto=format&fit=crop&w=650&q=40",
      "image_local": "/assets/images/10001.avif",
      "rating": 5,
      "in_stock": true,
      "size": 5,
      "best_seller": true
    }
    // More products...
  ]
}
```
> For more, see [`data/db.json`](https://github.com/arnobt78/Mock-Server--eBookStore/blob/main/data/db.json)

---

## Learning & Teaching Notes

- **Purpose:** This project is designed as a learning tool for developers to understand how to mock REST APIs, use authentication, and simulate a real backend for frontend development.
- **Modular Structure:** Easily add more entities or extend existing data.
- **Security:** Shows how to implement and test route protection in a mock server context.
- **Frontend Integration:** Works perfectly with any frontend (React, Angular, Vue, etc.) — just use the `/api` endpoints.
- **Customization:** Data, routes, and access rules can be easily edited for different scenarios.

---

## Full Code Example: Server Setup (`index.js`)

```javascript
import express from "express";
import jsonServer from "json-server";
import auth from "json-server-auth";

const server = express();
server.use((req, res, next) => {
    res.header('Access-Control-Allow-Origin', '*');
    res.header('Access-Control-Allow-Headers', '*');
    next();
});

const router = jsonServer.router('./data/db.json');
server.use('/api', router);
server.db = router.db;

const middlewares = jsonServer.defaults();
const rules = auth.rewriter({
    products: 444,
    featured_products: 444,
    orders: 660,
    users: 600
});

server.use(rules);
server.use(auth);
server.use(middlewares);
server.use(router);

server.listen(8000);
```

---

## Keywords

`express`, `json-server`, `mock api`, `authentication`, `json-server-auth`, `REST`, `node.js`, `eBookStore`, `api prototyping`, `learning`, `teaching`, `backend`, `routes`, `middleware`, `mock data`, `CORS`

---

## Conclusion

The **eBookStore Mock Server** is a robust and easy-to-use mock backend for learning, teaching, and rapid prototyping. With real-world structure and authentication, it empowers developers to quickly test and demo frontend applications without building a full backend. Customize the data, routes, and rules as needed — and start building today!

---
