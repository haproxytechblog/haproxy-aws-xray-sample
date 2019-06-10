FROM ubuntu:bionic

EXPOSE 514/udp

# Set the AWS region
ENV aws_region us-east-2

WORKDIR /app
RUN apt update && apt install -y wget
RUN wget https://s3.dualstack.$aws_region.amazonaws.com/aws-xray-assets.$aws_region/xray-daemon/aws-xray-daemon-3.x.deb
RUN dpkg -i aws-xray-daemon-3.x.deb

COPY cfg.yaml /etc/amazon/xray/
RUN sed -i "s/AWS_REGION/${aws_region}/g" /etc/amazon/xray/cfg.yaml

COPY 49-haproxy.conf /etc/rsyslog.d/
COPY init.sh .
RUN chmod +x ./init.sh

ENTRYPOINT /bin/bash -c ./init.sh