FROM node:16.9.0-alpine
WORKDIR /usr
COPY package.json ./
RUN ls -a
RUN yarn install
RUN yarn build
EXPOSE 8080
CMD ["node", "index.js"]