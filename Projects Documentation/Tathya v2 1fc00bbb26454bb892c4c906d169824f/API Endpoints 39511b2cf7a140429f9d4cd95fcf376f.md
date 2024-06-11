# API Endpoints

Iteration 1;

```jsx

//Products endpoints
GET "/api/v1/products"
GET "/api/v1/products/:productId"
POST "/api/v1/products"
PATCH "/api/v1/products/:productId"
DELETE "/api/v1/products/:productId"

//wishlist endpoint
// bookmark all the productId by the user
GET "/api/v1/wishlist"

//Cart Endpoints
GET "/api/v1/carts"
GET "/api/v1/carts/:orderId"
POST "/api/v1/carts"
PATCH "/api/v1/carts/:orderId"
DELETE "/api/v1/carts/:orderId"

// Authentication Endpoints
POST "/api/v1/auth/login"
POST "/api/v1/auth/register"
POST "/api/v1/auth/logout"
```

Iteration 2: