FROM node:lts-alpine3.16

ENV NODE_ENV production

RUN apk add --no-cache dumb-init && \
    mkdir -p /home/node/app && \
    chown -R node:node /home/node

WORKDIR /home/node/app 

COPY --chown=node:node package*.json ./

RUN npm ci --only=production && \
    npm cache clean –force

USER node

COPY --chown=node:node . .

EXPOSE 8080

CMD ["dumb-init", "node", "server.js"]