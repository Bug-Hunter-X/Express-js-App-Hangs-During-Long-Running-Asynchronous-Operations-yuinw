# Express.js Asynchronous Operation Timeout Bug

This repository demonstrates a common issue in Express.js applications: unresponsive servers due to long-running asynchronous operations.  The bug occurs when a route handler performs an asynchronous task (like a database query or a long-running computation) without proper handling of the asynchronous nature of the task.  If the operation takes longer than the default timeout, the server may appear to hang.

## Bug Description

The `bug.js` file contains an Express.js application with a route handler that simulates a long-running asynchronous operation using `setTimeout`.  This causes the server to be unresponsive for 5 seconds. In a real-world scenario, this could be a database query, a network request, or any other lengthy process. The issue is particularly insidious because it doesn't produce an obvious error message; the server simply stops responding.

## Solution

The `bugSolution.js` file demonstrates how to properly handle asynchronous operations.  We use Promises and `async/await` to efficiently manage asynchronous requests and prevent timeout issues.  We're also using error handling with `try...catch` blocks for better management of exceptions.

## How to Reproduce the Bug

1. Clone this repository.
2. Navigate to the directory containing `bug.js`.
3. Run `node bug.js`.
4. Attempt to access the server (e.g., using `curl http://localhost:3000` or a web browser).  Observe that the server is unresponsive for 5 seconds before responding.

## How to Implement the Solution

1. Refer to `bugSolution.js` for the corrected code.
2. Observe how asynchronous operations are managed using Promises and `async/await`.
3. Note how the solution uses `try...catch` to handle potential errors that could occur during an asynchronous operation.

## Key Learning Points

* Always handle asynchronous operations in Express.js route handlers properly to prevent timeout issues.
* Use Promises and `async/await` for efficient asynchronous code management.
* Implement robust error handling to gracefully handle potential exceptions during asynchronous operations.