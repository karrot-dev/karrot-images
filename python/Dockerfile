FROM debian:stretch

RUN apt-get update && \
    apt-get install -y \
        curl \
        gnupg gnupg2 gnupg1 \
        python3.5 \
        python3.5-dev \
        virtualenv

RUN curl -s https://deb.nodesource.com/setup_10.x | bash - && \
    apt-get update && \
    apt-get install -y nodejs

RUN apt-get install -y \
        build-essential

RUN curl -o /usr/local/bin/circleci \
        https://circle-downloads.s3.amazonaws.com/releases/build_agent_wrapper/circleci && \
    chmod +x /usr/local/bin/circleci

RUN apt-get install -y git

RUN apt-get install -y python3-pip

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" > \
      /etc/apt/sources.list.d/yarn.list && \
    apt-get update && apt-get install yarn

RUN apt-get update && \
    apt-get install -y wget rsync && \
    pip3 install --upgrade pip==10.0.1 pip-tools==2.0.2

COPY requirements.txt /tmp/
RUN pip3 install -r /tmp/requirements.txt
