# Intermittent Server Crash: Unhandled 'SIGPIPE' Error in Node.js

This repository demonstrates a common yet tricky Node.js issue: an intermittent server crash caused by an unhandled 'SIGPIPE' error. The error is particularly hard to debug because it's unpredictable.  The solution involves properly handling the 'close' event on the response object.

## Bug Description

A Node.js HTTP server crashes sporadically with an unhandled 'SIGPIPE' error. The cause is usually abrupt client disconnections while the server is still sending data.  The server doesn't gracefully handle the connection closure, leading to the crash.

## Solution

The solution involves using the 'close' event listener on the response object to detect when a client connection is closed prematurely. This allows for more controlled handling, preventing the 'SIGPIPE' error.  This approach addresses the root cause of the problem, ensuring the server's stability. 