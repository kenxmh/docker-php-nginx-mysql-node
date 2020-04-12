ARG NODE_VERSION
FROM node:${NODE_VERSION}

# ENV NODE_ENV=production
# ENV HOST 0.0.0.0

WORKDIR /www

#此为cnpm淘宝镜像
RUN npm config set registry https://registry.npm.taobao.org
# RUN npm install
# RUN npm run build
# CMD ["npm", "start"]