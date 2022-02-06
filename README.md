# Setup of PWA app

## Pull the latest shinyproxy image
```
docker pull openanalytics/shinyproxy:latest
```

## Build the shinyMobile pwa test-app image
```
docker build -t testapp ./pwa-testapp
```

## Start the shinyproxy
```
export DOCKERID=$(getent group docker | cut -d: -f3)
docker-compose -f ./shinyproxy/shinyproxy_docker.yml up
```

## Alternatlively, test the shiny app only 
```
docker-compose -f ./pwa-testapp/test-app-only.yml up
```

## Or test whith shinyproxy as standalone 
```
wget https://www.shinyproxy.io/downloads/shinyproxy-2.6.0.jar -O ./shinyproxy-standalone/shinyproxy.jar
java -jar ./shinyproxy-standalone/shinyproxy.jar     
```