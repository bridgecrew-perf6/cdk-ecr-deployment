# Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved.
# SPDX-License-Identifier: Apache-2.0


FROM lambci/lambda:build-go1.x

USER root

ADD . /opt/awscli

RUN yum -y install \
    gpgme-devel \
    btrfs-progs-devel \
    device-mapper-devel \
    libassuan-devel \
    libudev-devel

ENV GOOS=linux \
    GOARCH=amd64 \
    GOPROXY=https://goproxy.cn,https://goproxy.io,direct

# run tests
WORKDIR /opt/awscli

RUN make test

ENTRYPOINT [ "/bin/bash" ]