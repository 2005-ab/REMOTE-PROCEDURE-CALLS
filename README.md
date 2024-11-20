# Remote Procedure Calls (RPC) Using xmlrpc_server in Python

This repository demonstrates how to implement Remote Procedure Calls (RPC) in Python using the `xmlrpc.server` module, which is part of the Python standard library. RPC allows you to invoke functions or methods on a remote server as if they were local, making it ideal for building distributed systems and client-server applications.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Example](#example)
- [Contributing](#contributing)

## Introduction

The `xmlrpc.server` module in Python provides a simple way to implement an XML-RPC server. XML-RPC is a protocol that allows remote procedure calls to be made over HTTP, with XML encoding the data. This repository provides examples of setting up an XML-RPC server and client in Python, enabling easy communication between remote systems.

## Features
- Simple implementation of an XML-RPC server and client in Python
- Supports remote procedure calls with data passing and return values
- Uses standard Python libraries (`xmlrpc.server` and `xmlrpc.client`)
- Easy-to-understand example code for both server and client

## Installation

To use this repository, clone it to your local machine:

```bash
git clone https://github.com/yourusername/xmlrpc-server-python.git
cd xmlrpc-server-python
```
### Requirements

- Python 3.6+ (No additional dependencies are required, as `xmlrpc.server` is part of the Python standard library)

## Usage
Running the Server
To start the XML-RPC server, simply run the server script
```bash
python server.py
```
The server will start and listen for incoming RPC requests at http://localhost:8000.
## Example
Server Code (server.py)
This is the code for the server that defines a function to be called remotely:
```bash
from xmlrpc.server import SimpleXMLRPCServer

# Function to be exposed to the client
def add(a, b):
    return a + b

# Create the server
server = SimpleXMLRPCServer(('localhost', 8000))
print("Server is running on http://localhost:8000")

# Register the function so it's available for remote calls
server.register_function(add, 'add')

# Run the server
server.serve_forever()
```
Client Code (client.py)
This client connects to the server and calls the remote procedure:
```bash
import xmlrpc.client

# Connect to the server
server = xmlrpc.client.ServerProxy('http://localhost:8000')

# Call the remote function
result = server.add(5, 3)

# Print the result
print("Result from server:", result)
```
### How it Works:
The server listens for incoming requests and registers the add function as a callable method for clients.
The client connects to the server and calls the add function, passing arguments (in this case, 5 and 3).
The server executes the function and sends back the result (8) to the client.
The client prints the result received from the server.

## Contributing
Contributions are welcome! If you have any improvements, bug fixes, or suggestions, feel free to fork the repository and submit a pull request. For any issues or questions, please open an issue in the GitHub repository.

