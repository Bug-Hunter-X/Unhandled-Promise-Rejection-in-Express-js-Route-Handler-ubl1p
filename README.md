# Unhandled Promise Rejection in Express.js Route Handler

This repository demonstrates a common error in Node.js Express applications: unhandled promise rejections.  The `bug.js` file contains an Express.js route handler that performs an asynchronous operation. However, it fails to properly handle potential errors from that operation.  This results in the application crashing silently. The `bugSolution.js` file provides a corrected version with comprehensive error handling.

## Setup

1. Clone the repository.
2. Navigate to the repository directory.
3. Run `npm install express` to install the required dependencies.
4. Run `node bug.js` to observe the unhandled rejection.  (Then run `node bugSolution.js` to see the fix)

## Problem

The asynchronous `someAsyncOperation` function simulates a situation where a database query or external API call could fail.  The `catch` block in the route handler is missing. Without that catch block, any error thrown inside `someAsyncOperation` will cause the server to crash unexpectedly, without any indication of what went wrong.

## Solution

The solution involves adding a robust `catch` block to handle any rejected promises. This includes logging the error for debugging purposes, sending an appropriate error response to the client (e.g., a 500 Internal Server Error), or taking other necessary actions (e.g., retrying the operation).
