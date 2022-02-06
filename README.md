# Setup of PWA app


## Pull the latest shinyproxy image
docker pull openanalytics/shinyproxy:latest

## Build the shinyMobile pwa test-app image
docker build -t testapp ./pwa-testapp


## Start the shinyproxy
export DOCKERID=$(getent group docker | cut -d: -f3)

docker-compose -f ./shinyproxy/shinyproxy_docker.yml up


## Alternatlively, test the shiny app only 
docker-compose -f ./pwa-testapp/test-app-only.yml up