# Setup of PWA app

docker pull openanalytics/shinyproxy:latest

docker build -t testapp .

docker-compose -f .\shinyproxy_docker.yml up