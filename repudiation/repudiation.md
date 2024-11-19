# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Run the server __insecure.ts__.

3. Pretend to be a malicous user and interact with the services by sending requests from the browser.

4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.
    No logging to track back problem and debug issues. 
    No monitor of system events.
2. Briefly explain why the vulnerability is addressed in __secure.ts__.
    Use bunch of middleware function to implement logging message, requests, and errors. 
3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?
    Middleware pattern, using request and response chain. 
    
    These middleware functions allows focuses on logging, error handling process in separate concerns, we are able to modify request and responses, and this flow proecesses requests sequentially before reaching route handlers. Like the logging middleware captures request details and timestamps, while the error handling middleware catches and logs exceptions. 