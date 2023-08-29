FROM node:18.17.0 as builder

RUN mkdir -p /usr/src/app

WORKDIR /usr/src/app

COPY package*.json /package.json
COPY yarn*.lock /yarn.lock

RUN yarn install

COPY ./ /usr/src/app

RUN yarn build

FROM nginx

# RUN rm -rf /etc/nginx/conf.d

COPY --from=builder /usr/src/app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]