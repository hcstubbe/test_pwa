FROM openjdk:11-jre

RUN mkdir -p /opt/shinyproxy/
RUN wget https://www.shinyproxy.io/downloads/shinyproxy-2.6.0.jar -O /opt/shinyproxy/shinyproxy.jar

RUN mkdir /opt/shinyproxy/templates
COPY ./templates/test /opt/shinyproxy/templates/test
COPY ./application/application_test.yml /opt/shinyproxy/application.yml

WORKDIR /opt/shinyproxy/
CMD ["java", "-jar", "/opt/shinyproxy/shinyproxy.jar"]