FROM node:18.17.0 as builder

WORKDIR /var/jenkins_home/workspace/ec2_test/deploy_test

COPY yarn*.lock package*.json ./

RUN yarn install

COPY . .

RUN yarn build
FROM nginx:stable-alpine as production-stage

COPY --from=builder /var/jenkins_home/workspace/ec2_test/deploy_test/dist /usr/share/nginx/html
#COPY --from=build-stage /var/jenkins_home/workspace/deploytest/testproject_react/deploy_conf/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g","daemon off;"]
