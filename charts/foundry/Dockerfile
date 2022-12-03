FROM ubuntu:latest
EXPOSE 30000

ARG TOKEN_URL

RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install -y libssl-dev curl wget unzip

RUN curl -sL https://deb.nodesource.com/setup_14.x | bash -
RUN apt-get install -y nodejs

RUN mkdir /foundry_data
RUN mkdir /home/foundry

WORKDIR /home/foundry
RUN wget -O foundryvtt.zip "${TOKEN_URL}"
RUN unzip foundryvtt.zip

CMD node /home/foundry/resources/app/main.js --dataPath=/foundry_data
