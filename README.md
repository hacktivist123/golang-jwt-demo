# Golang JWT Demo

This Repo demonstrates a simple JSON Web Token Implementation in Golang.

## Overview

This application shows how to implement JWT authentication in a Go application using the Echo web framework and RSA signing method. It demonstrates:

- RSA key-based JWT token generation
- Custom claims implementation
- Protected routes with JWT authentication
- Echo middleware configuration

## Usage

1. Start the server:

   ```bash
   go run main.go
   ```

2. The server will start at `http://localhost:1323` with the following endpoints:

   - `GET /`: Public route accessible without authentication
   - `POST /login`: Authenticate to get a JWT token
   - `GET /restricted`: Protected route requiring a valid JWT token

3. To get a JWT token, send a POST request to `/login`:

   ```bash
   curl -X POST -d "username=jon&password=shhh!" http://localhost:1323/login
   ```

4. Use the returned token to access the protected route:

   ```bash
   curl -H "Authorization: Bearer YOUR_TOKEN" http://localhost:1323/restricted
   ```

## Implementation Details

- Uses RSA256 signing method with public/private key pairs
- Custom claims include username and admin status
- Tokens expire after 72 hours
- Echo framework handles routing and middleware
- Authentication uses the echo-jwt middleware

## References

- [echo JWT Cookbook](https://echo.labstack.com/docs/cookbook/jwt)
