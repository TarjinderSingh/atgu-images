FROM rocker/tidyverse:latest

LABEL maintainer "Tarjinder Singh <tsingh@broadinstitute.org>"

ENV USER="rstudio" PASSWORD="admin" 
ENV HOME="/home/user"

# Create new user
RUN useradd user \
	&& echo "user:admin" | chpasswd \
	&& mkdir -p /home/user \
	&& chown user:user /home/user \
	&& addgroup user staff \
	&& usermod -aG root user

WORKDIR /home/user/

RUN mkdir -p /home/user/repos/ \
	&& mkdir -p /home/user/data/

RUN apt-get update && apt-get install -y curl

RUN curl -sSL https://sdk.cloud.google.com | bash \
	&& mkdir -p /opt/google-cloud-sdk/
	
ENV PATH $PATH:/home/user/google-cloud-sdk/bin/
RUN echo "export PATH=$PATH:/home/user/google-cloud-sdk/bin/" >> /home/user/.bash_profile

EXPOSE 4040 8787

RUN chown -R user:user /home/user/*

ENTRYPOINT /init