# 
# This file is part of the aws-devops distribution (https://github.com/hcary/aws-devops).
# Copyright (c) 2019 Harvey Cary.
# 
# This program is free software: you can redistribute it and/or modify  
# it under the terms of the GNU General Public License as published by  
# the Free Software Foundation, version 3.
#
# This program is distributed in the hope that it will be useful, but 
# WITHOUT ANY WARRANTY; without even the implied warranty of 
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU 
# General Public License for more details.
#
# You should have received a copy of the GNU General Public License 
# along with this program. If not, see <http://www.gnu.org/licenses/>.
#
FROM ubuntu:18.04

RUN apt-get -y update && \
    apt-get -y upgrade && \
    apt-get -y install unzip python3 python tar npm python3-pip
  #ln -s /usr/bin/python3 /usr/bin/python
#RUN pip3 install awscli --upgrade --user

#
# Install AWS CLI
WORKDIR /tmp/
ADD https://s3.amazonaws.com/aws-cli/awscli-bundle.zip /tmp/
RUN unzip /tmp/awscli-bundle.zip
RUN /tmp/awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
RUN rm -rf /tmp/awscli-bundle.zip /tmp/awscli-bundle

ADD https://amazon-eks.s3-us-west-2.amazonaws.com/1.13.7/2019-06-11/bin/linux/amd64/kubectl /usr/bin/kubectl
RUN chmod +x /usr/bin/kubectl

ADD https://amazon-eks.s3-us-west-2.amazonaws.com/1.13.7/2019-06-11/bin/linux/amd64/aws-iam-authenticator \
    /usr/bin/aws-iam-authenticator
RUN chmod +x /usr/bin/aws-iam-authenticator

#curl --silent --location "https://github.com/weaveworks/eksctl/releases/download/latest_release/eksctl_Linux_amd64.tar.gz" | tar xz -C /tmp

ADD https://github.com/weaveworks/eksctl/releases/download/latest_release/eksctl_Linux_amd64.tar.gz /tmp/
RUN tar xzf /tmp/eksctl_Linux_amd64.tar.gz -C /usr/bin/ && \
    chmod +x /usr/bin/eksctl && \
    rm -f /tmp/eksctl_Linux_amd64.tar.gz

#RUN npm install -g aws-cdk
#RUN pip3 install --upgrade aws-cdk.core
RUN pip3 install boto3

WORKDIR /