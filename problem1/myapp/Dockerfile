# single stage
##############
# FROM node
# WORKDIR /app
# copy package*.json ./
# RUN npm install 
# COPY . .
# EXPOSE 3000
# CMD ["npm","start"]

# sudo docker build -t my-app:1.0 .
# sudo docker images
# sudo docker run -it --name myapp-cont -p 3001:3000  my-app:1.0

############################################################################
# multi stage
##############
FROM node:alpine3.16 AS builder
WORKDIR /app
copy package*.json ./
RUN npm install 
COPY . .
RUN npm run build 

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
ENTRYPOINT ["nginx","-g","daemon off;"]


