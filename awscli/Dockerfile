## Adopted from https://github.com/aws/aws-codebuild-docker-images/blob/master/ubuntu/standard/2.0/Dockerfile
FROM ubuntu:20.04

RUN set -ex \
    && apt-get update \
    && mkdir ~/.ssh \
    && touch ~/.ssh/known_hosts \
    && DEBIAN_FRONTEND=noninteractive \
       apt-get install -y --no-install-recommends \
       wget curl git ca-certificates fakeroot jq inotify-tools bash busybox unzip s3cmd \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean

RUN set -ex \
    && curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && ./aws/install


RUN addgroup --gid 1000 appgroup  && useradd --create-home --gid appgroup --uid 1000 user

WORKDIR "/home/user"

USER user