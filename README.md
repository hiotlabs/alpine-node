# alpine-node
Based on [mhart/alpine-node](https://hub.docker.com/r/mhart/alpine-node/) minimal
node.js built on Alpine Linux.

We're installing npm packages one level above the `/src/app` folder.
Modules will still be found but won't be overridden when mounting
the project directory for development.

## Use in development setup
Dockerfile:

```
FROM hiotlabs/alpine-node:latest
RUN npm install -g supervisor
```

docker-compose.yml:

```
node:
  build: .
  volumes:
    - .:/src/app
  command: supervisor -e js,json app.js
```

## Credits
Ideas come from [here](http://www.grahamgilchrist.com/blog/2015/05/13/node-packages-docker-and-node-onbuild-container) and [there](https://github.com/b00giZm/docker-compose-nodejs-examples).
