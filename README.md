# Shiny progressive web app (PWA) deployment using ShinyProxy

## Clone this repository
```
git clone https://github.com/hcstubbe/test_pwa.git
cd test_pwa
```

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
This is the only option I got to work right now.
```
docker-compose -f ./pwa-testapp/test-app-only.yml up
```

## Or test whith shinyproxy as standalone 
This was tested using the app_direct path.
```
wget https://www.shinyproxy.io/downloads/shinyproxy-2.6.0.jar -O ./shinyproxy-standalone/shinyproxy.jar
cd shinyproxy-standalone
sudo java -jar shinyproxy.jar     
```

# Docker engine setup
```
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "debug": false,
  "experimental": false,
  "features": {
    "buildkit": true
  },
  "hosts": [
    "tcp://127.0.0.1:2375"
  ],
  "insecure-registries": [],
  "registry-mirrors": []
}
```
