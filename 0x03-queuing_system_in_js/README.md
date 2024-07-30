# 0x03. Queuing System in JS

## Redis and Node.js Project

This project demonstrates how to interact with a Redis server using Node.js. It includes examples of running Redis server operations, storing hash values, handling asynchronous operations, and utilizing Kue for queue management. Additionally, the project showcases building a basic Express app that interacts with a Redis server and queue system.

## Table of Contents

- [Resources](#resources)
- [Learning Objectives](#learning-objectives)
- [Requirements](#requirements)
- [Project Setup](#project-setup)
- [Usage](#usage)
- [Required Files](#required-files)

## Resources

Read or watch:
- [Redis quick start](https://redis.io/topics/quickstart)
- [Redis client interface](https://redis.io/topics/clients)
- [Redis client for Node JS](https://github.com/NodeRedis/node-redis)
- [Kue](https://github.com/Automattic/kue) (deprecated but still used in the industry)

## Learning Objectives

By the end of this project, you will be able to explain:
- How to run a Redis server on your machine
- How to run simple operations with the Redis client
- How to use a Redis client with Node.js for basic operations
- How to store hash values in Redis
- How to handle asynchronous operations with Redis
- How to use Kue as a queue system
- How to build a basic Express app interacting with a Redis server
- How to build a basic Express app interacting with a Redis server and queue system

## Requirements

- All code will be compiled/interpreted on Ubuntu 18.04, Node 12.x, and Redis 5.0.7
- All files should end with a new line
- A `README.md` file, at the root of the project folder, is mandatory
- Your code should use the `.js` extension

## Project Setup

1. Clone the repository:
    ```bash
    git clone https://github.com/your_username/your_repo.git
    cd your_repo
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Start the Redis server:
    ```bash
    redis-server
    ```

## Usage

### Running Redis Client Operations

1. Connect to Redis using the client:
    ```bash
    redis-cli
    ```

2. Run simple Redis operations:
    ```bash
    SET key value
    GET key
    ```

### Using Redis with Node.js

1. Create a new file `app.js` and include basic Redis operations:
    ```javascript
    const redis = require('redis');
    const client = redis.createClient();

    client.on('connect', function() {
        console.log('Connected to Redis...');
    });

    client.set('key', 'value', redis.print);
    client.get('key', function(err, reply) {
        console.log(reply); // Will print 'value'
    });
    ```

2. Run the Node.js application:
    ```bash
    node app.js
    ```

### Using Kue as a Queue System

1. Create a new file `queue.js` and include Kue setup:
    ```javascript
    const kue = require('kue');
    const queue = kue.createQueue();

    queue.process('task', function(job, done) {
        console.log('Processing task:', job.data);
        done();
    });

    const job = queue.create('task', {
        title: 'My first task',
        data: 'Task data'
    }).save(function(err) {
        if (!err) console.log(job.id);
    });
    ```

2. Run the queue system:
    ```bash
    node queue.js
    ```

## Required Files

### `package.json`
```json
{
  "name": "redis-node-project",
  "version": "1.0.0",
  "description": "A project to demonstrate Redis and Node.js integration",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "redis": "^3.0.2",
    "kue": "^0.11.6",
    "express": "^4.17.1"
  }
}
```
.babelrc
```
{
  "presets": ["@babel/preset-env"]
}
```
Don't forget to run:
```
npm install
```




