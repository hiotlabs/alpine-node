FROM mhart/alpine-node:4.2.2

RUN mkdir -p /src/app
WORKDIR /src/app

ONBUILD RUN apk add --update make gcc g++ python

# Install packeges to a directory above the project. Modules will still be found
# but won't be overridden when mounting the project directory for development.
# Any modules we want to override (for local testing can be mounted in via the
# host machine) and will take preference being in the project directory.
ONBUILD WORKDIR /src
ONBUILD COPY package.json /src/
ONBUILD RUN npm install

ONBUILD RUN apk del make gcc g++ python && \
          rm -rf /tmp/* /var/cache/apk/* /root/.npm /root/.node-gyp

ONBUILD COPY . /src/app

# Reset working dir for running project.
ONBUILD WORKDIR /src/app

CMD [ "npm", "start" ]
