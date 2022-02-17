---
layout: post
title: Deepak Dargade
subheading: I'm a Mumbai-based Entrepreneur, Ruby on Rails monomaniac and Food enthusiast.
headline: Excerpt from Docker for Rails Developers - Part 1
datePublished: 02 Feb 2022, Mumbai
datetime: 2022-02-02T20:55
---

<h3>Docker for rails developers:</h3>

1. We ran our first ever Docker command, a helloworld Ruby script, without needing Ruby installed on our machine.
```
$ docker run ruby:2.6 ruby -e "puts :hello"
```
2. We saw how to list our running containers with docker ps and all containers (including stopped ones) with docker ps -a.
3. We deleted our old containers with docker rm <container id> and saw how to create throwaway containers using the docker run’s --rm option.
4. We generated a new Rails project using a container by:
    - Starting an interactive Bash shell running inside a container
    ```
    $ docker run -i -t --rm -v ${PWD}:/usr/src/app ruby:2.6 bash
    ```
    - Installing the Rails gem inside the container
    ```
    root@0c286e8bda42:/usr/src/app# gem install rails
    ```
    - Using the freshly installed Rails gem to generate our project
    ```
    root@0c286e8bda42:/usr/src/app# rails new myapp --skip-test --skip-bundle
    ```
5. We saw our first, rough-and-ready Dockerfile designed to allow us to run our app with a Rails server:
```
> FROM ruby:2.6
> RUN apt-get update -yqq
> RUN apt-get install -yqq --no-install-recommends nodejs
> COPY . /usr/src/app/
> WORKDIR /usr/src/app
> RUN bundle install
```
6. We built our custom image from this Dockerfile with:
```
docker build .
```
7. We listed the images on our system by issuing:
```
docker images
```
8. We started up a Rails server to run our app with:
```
docker run -p 3000:3000 a1df0eddba18 bin/rails s -b 0.0.0.0
```
9. And we saw it running in a browser on http://localhost:3000.
