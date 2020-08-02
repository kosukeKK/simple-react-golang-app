FROM "node:12.18.0-alpine"
WORKDIR /opt/app
COPY app/package.json  /opt/app/
COPY app/yarn.lock /opt/app/
RUN yarn install
COPY app /opt/app
