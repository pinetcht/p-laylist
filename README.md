# p-laylist

[![tests](https://github.com/tylerheadley/twitter-clone/actions/workflows/tests.yml/badge.svg)](https://github.com/tylerheadley/twitter-clone/actions/workflows/tests.yml)

## Table of Contents

1. [Overview](#overview)
2. [Tech Stack](#tech-stack)
3. [Build Instructions](#build-instructions)

## Overview 

Have you ever been frustrated with Spotify recommending the same songs repeatedly, even when your interests change? Or wished you could expand your music taste and fill in the gaps in your playlists? What about that friend with impeccable music taste whose playlists you can’t access because they use Apple Music? Our project tackles these issues by developing an AI-powered web app for collaborative music recommendations. 

Our platform will generate daily, personalized playlists by using a hybrid of collaborative filtering and content-based recommendation techniques. The core of our product is a recommendation engine that analyzes both user behavior and song characteristics. In addition, we plan to integrate social media-like features for collaborative music sharing, song reviews, and discussions, enhancing community interaction around music discovery.

On the technical side, our recommendation model will employ an ensemble approach. We’ll combine deep learning for music content analysis with traditional recommendation algorithms like matrix factorization or graph-based models for collaborative filtering. By tuning parameterized weights, users can receive diverse recommendations, such as music beyond their typical taste, emerging artists, or popular picks overall. Our ultimate goal is to offer a seamless, engaging experience, connecting users across various streaming platforms, and providing them with dynamic music recommendations based on their playlists and listening habits.

## Tech Stack 

 - Python: Used for backend development.
 - Flask: Micro web framework used for server-side logic.
 - HTML/CSS: Frontend design and styling.
 - Jinja2: Templating engine for rendering dynamic content.
 - PostgreSQL: Database management system.
 - Docker (+ Docker Compose): Containerization for development and production environments.
 - Nginx: High-performance web server and reverse proxy server.
 - Gunicorn: WSGI (Web Server Gateway Interface) HTTP server.
 - AWS EC2: Cloud computing and hosting.
 - GitHub Actions: Implemented for continuous integration.


## Build Instruction

**To bring up the services, follow these steps:**

First, clone this repository and navigate to the project directory.

To build and run the development containers:

```
$ docker-compose up -d --build
```

Access the Flask app at http://localhost:1341/. 

Access the frontend app at http://localhost:3000/.

To stop the containers:

```
$ docker-compose down
```

You may include the -v flag at the end of this command to delete the postgres volume.

For production, use the docker-compose.prod.yml file instead. 
The production environment includes a few differences from the development build. The most substantial difference is the use of Nginx and Gunicorn as a WSGI server.
Note that you will need to add your own `.env.prod.db` text file containing database credentials. My file has 3 environment variables, `POSTGRES_USER`,`POSTGRES_PASSWORD`, and `PGUSER`.

Build and run the production containers, and initialize the PostgreSQL database:

```
$ docker-compose -f docker-compose.prod.yml up -d --build
```

Access the production Flask app at http://localhost:80/.


To stop the production containers:

```
$ docker-compose -f docker-compose.prod.yml down -v
```

