FROM node:22.12.0-alpine
WORKDIR /app
RUN apk add bash
COPY ./app .
RUN npm install
CMD ["npm", "start"]
