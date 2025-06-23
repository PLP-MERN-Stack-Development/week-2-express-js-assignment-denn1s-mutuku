[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19834633&assignment_repo_type=AssignmentRepo)
# Express.js RESTful API Assignment

This assignment focuses on building a RESTful API using Express.js, implementing proper routing, middleware, and error handling.

## Assignment Overview

You will:
1. Set up an Express.js server
2. Create RESTful API routes for a product resource
3. Implement custom middleware for logging, authentication, and validation
4. Add comprehensive error handling
5. Develop advanced features like filtering, pagination, and search

## Getting Started

1. Accept the GitHub Classroom assignment invitation
2. Clone your personal repository that was created by GitHub Classroom
3. Install dependencies:
   ```
   npm install
   ```
4. Run the server:
   ```
   npm start
   ```

## Files Included

- `Week2-Assignment.md`: Detailed assignment instructions
- `server.js`: Starter Express.js server file
- `.env.example`: Example environment variables file

## Requirements

- Node.js (v18 or higher)
- npm or yarn
- Postman, Insomnia, or curl for API testing

## API Endpoints

The API will have the following endpoints:

- `GET /api/products`: Get all products

app.get('/api/products', (req, res) => {
  res.json(products);
});


- `GET /api/products/:id`: Get a specific product

app.get ('/api/products/:id', (req, res) => {
  const productId = req.params.id;
  const product = products.find(p => p.id === productId);
  
  if (product) {
    res.json(product);
  } else {
    res.status(404).json({ message: 'Product not found' });
  }
});


- `POST /api/products`: Create a new product

app.post('/api/products', (req, res) => {
  const newProduct = {
    id: uuidv4(), // Generate a unique ID for the new product
    ...req.body // Spread the request body into the new product object
  };

  products.push(newProduct); // Add the new product to the in-memory database
  res.status(201).json(newProduct); // Respond with the created product
});



- `PUT /api/products/:id`: Update a product

app.put('/api/products/:id', (req, res) => {
  const productId = req.params.id;
  const productIndex = products.findIndex(p => p.id === productId);

  if (productIndex !== -1) {
    const updatedProduct = {
      ...products[productIndex],
      ...req.body // Update the product with the request body
    };
    
    products[productIndex] = updatedProduct; // Update the product in the in-memory database
    res.json(updatedProduct); // Respond with the updated product
  } else {
    res.status(404).json({ message: 'Product not found' });
  }
});



- `DELETE /api/products/:id`: Delete a product

app.delete('/api/products/:id', (req, res) => {
  const productId = req.params.id;
  const productIndex = products.findIndex(p => p.id === productId);

  if (productIndex !== -1) {
    products.splice(productIndex, 1); // Remove the product from the in-memory database
    res.status(204).send(); // Respond with no content
  } else {
    res.status(404).json({ message: 'Product not found' });
  }
});



## Submission



Your work will be automatically submitted when you push to your GitHub Classroom repository. Make sure to:

1. Complete all the required API endpoints
2. Implement the middleware and error handling
3. Document your API in the README.md
4. Include examples of requests and responses

## Resources

- [Express.js Documentation](https://expressjs.com/)
- [RESTful API Design Best Practices](https://restfulapi.net/)
- [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) 