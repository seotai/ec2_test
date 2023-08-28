FROM node:18.16.1 as builder

WORKDIR /var/jenkins_home/workspace/ec2_test/deploy_test

COPY . .

RUN yarn install

RUN yarn build

FROM nginx:stable-alpine as production-stage

COPY --from=builder /var/jenkins_home/workspace/ec2_test/deploy_test/dist /usr/share/nginx/html
# COPY --from=builder /var/jenkins_home/workspace/ec2_test/deploy_test/deploy_conf/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD [ "nginx", "-g", "daemon off" ]