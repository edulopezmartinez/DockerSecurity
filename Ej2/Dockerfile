# docker build -t fuentecilla86/ubuntu .

FROM fuentecilla86/ubuntu

RUN apt-get update
RUN apt-get install -y nginx

CMD ["nginx", "-g", "daemon off;"]
