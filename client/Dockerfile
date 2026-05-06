FROM node:16-alpine as todo-app-build
WORKDIR /client
COPY package.json yarn.lock README.md ./
RUN yarn
COPY ./public ./public
COPY ./src ./src
ARG REACT_APP_baseAPIURL
ENV REACT_APP_baseAPIURL=$REACT_APP_baseAPIURL
RUN yarn build

FROM nginx:latest
LABEL maintainer=Aamir-Pinger
COPY --from=todo-app-build /client/build/ /usr/share/nginx/html
EXPOSE 80