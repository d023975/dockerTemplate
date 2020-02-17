FROM openjdk:8-slim

# install jq (json input processor) install curl

RUN apt-get -y update && apt-get -yq upgrade && apt-get  -yq install jq curl

RUN mkdir -p /opt/dynatrace
RUN mkdir -p /opt/supertest

COPY blub.jar /opt/supertest
COPY start.sh /opt/supertest
WORKDIR /opt/supertest

ENTRYPOINT [ "/bin/sh" "opt/supertest/start.sh" ]