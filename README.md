# Silent Crash in Express.js Due to Unhandled Promise Rejections

This repository demonstrates a common error in Express.js applications where asynchronous operations within middleware functions might throw errors that are not properly handled, leading to silent crashes.

## Bug

The `bug.js` file contains an Express.js application with a route handler that performs an asynchronous operation (`someAsyncOperation`). This operation randomly simulates an error.  The error handling within the `.catch` block is insufficient because it only logs the error to the console; it does not send an error response to the client, nor does it gracefully shut down the server.

## Solution

The `bugSolution.js` file provides a corrected version.  The solution uses a `try...catch` block within an `async` function to handle the error.  If an error occurs, the solution sends an appropriate error response to the client (status 500) and logs the error for debugging purposes. This prevents the server from crashing silently and gives the client informative feedback.