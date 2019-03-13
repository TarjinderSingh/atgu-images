FROM continuumio/anaconda3

LABEL maintainer "Tarjinder Singh <tsingh@broadinstitute.org>"

ENV HOME="/home/user/"

WORKDIR /home/user/

RUN apt-get update \
	&& apt-get install -y bash emacs \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

RUN curl -sSL https://sdk.cloud.google.com | bash \
	&& mkdir -p /opt/google-cloud-sdk/

ENV PATH $PATH:/home/user/google-cloud-sdk/bin/
RUN echo "export PATH=$PATH:/home/user/google-cloud-sdk/bin/" >> /home/user/.bash_profile

EXPOSE 4040 8080 8888

ENTRYPOINT [ "jupyter notebook --no-browser" ]