FROM node:alpine

ENV DB_HOST=localhost
ENV DB_PORT=3306
ENV USER=root
ENV PASSWORD=changeit
ENV APP_ROOT=/app
ENV APP_PORT=3000
ENV APP_RETRIES=3
ENV RETRY_INTERVAL=30

WORKDIR ${APP_ROOT}

ADD config config
ADD public public
ADD views views
ADD package.json .
ADD main.js .

RUN apk add curl

RUN npm i

EXPOSE ${APP_PORT}

HEALTHCHECK --interval=30s --timeout=30s --retries=3 \
  CMD curl -f http://localhost:${APP_PORT}/health >> /dev/null || exit 1

ENTRYPOINT [ "node", "main.js" ]