#syntax=docker/dockerfile:1

FROM node:18-alpine as base
WORKDIR /src
COPY ./.. .
RUN npm install && npm run compile

FROM node:18-alpine
WORKDIR /src
COPY --from=base /src/dist ./dist
COPY ./../package*.json .
RUN npm install --production
CMD ["node", "dist/index.js"]
EXPOSE 4000