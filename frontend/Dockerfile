FROM node:alpine AS build
WORKDIR /app
COPY package*.json .
RUN npm ci
COPY . .
RUN npm run build
RUN npm install -g serve

EXPOSE ${PORT}
CMD [ "sh", "-c", "serve -s build -l ${PORT}" ] 
