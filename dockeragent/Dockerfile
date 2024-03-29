FROM ubuntu:20.04
RUN DEBIAN_FRONTEND=noninteractive apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get upgrade -y

RUN DEBIAN_FRONTEND=noninteractive apt-get install -y -qq --no-install-recommends \
    apt-transport-https \
    apt-utils \
    ca-certificates \
    curl \
    git \
    iputils-ping \
    jq \
    lsb-release \
    software-properties-common \
    openssh-client \
    python3-pip

RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

# Can be 'linux-x64', 'linux-arm64', 'linux-arm', 'rhel.6-x64'.
ENV TARGETARCH=linux-x64

WORKDIR /azp

COPY . .
RUN chmod +x start.sh

RUN chmod +x lint.sh

RUN pip3 install --upgrade pip && \
    pip3 install -r dev-requirements-py3.txt && \
    pip3 list && \
    ./lint.sh && \
    pip3 install . && \
    pytest tests

ENTRYPOINT [ "./start.sh" ]
