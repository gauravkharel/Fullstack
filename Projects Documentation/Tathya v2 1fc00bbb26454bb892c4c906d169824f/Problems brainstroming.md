### 1 Building cart - Problem 
Cart should retrieve from API and store in react context. And the context should update AddToCart function and update cart in the backend using react-query mutation and in the frontend in components.

In each AddToCart function, the cart gets updated and it should reflected in both NavBar and CartLayout component. Also, the changes are made in the server as well. 

### 2 Sending user-id to every authenticated request. 
```
app.use(verifyJWT);
app.use("/products", require("./routes/api/product"));
app.use("/carts", require("./routes/api/cart"));
// app.use("/api/uplwwoadthing", require('./routes/uploadthing'))
app.use("/orders", require("./routes/api/order"));

app.use(errorHandler, errorLogger, errorNotFound);

app.listen(PORT, () => console.log(`Server running at port ${PORT}`));
```
```
verifyJWT.js
const jwt = require("jsonwebtoken");
const prisma = require("../lib/db");
require("dotenv").config();

const verifyJWT =async (req, res, next) => {
  //gets the header from request
  const authHeader = req.headers.authorization || req.headers.Authorization;
  //for roles change upper code to
  if (!authHeader?.startsWith("Bearer ")) return res.sendStatus(401);
  // save the token
  const token = authHeader.split(' ')[1];
  //verify it
  jwt.verify(
    token,
    process.env.ACCESS_TOKEN_SECRET,
    (err, decoded) => {
        if (err) return res.sendStatus(403, "here it comes"); //invalid token
        req.email= decoded.email;
        console.log(
          "re: ",req.email, "de", decoded.email
        )
        next();
    }
);

const findUser = await prisma.user.findUnique({
  where: {
    email: req.email,
  },
});

return findUser.id;
};

module.exports = verifyJWT;

```

What I want is somehow, the user gets the userId in the request. I don't know how to do it?


### Listing now needed features.
1. Filters in product page. 
2. And making the order flow. 
3. Adding picture using EC2 Instance. 
4. Making deployment now. 
