# Setup of PWA app

docker pull openanalytics/shinyproxy:latest

docker build -t testapp .

export DOCKERID=$(getent group docker | cut -d: -f3)

docker-compose -f .\shinyproxy_docker.yml up