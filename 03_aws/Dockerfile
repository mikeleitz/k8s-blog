FROM python:alpine

ARG CLI_VERSION=1.16.200

RUN pip install --no-cache-dir awscli==$CLI_VERSION && \
    mkdir /root/.aws

RUN apk update && apk add bash curl

# Install kubectl
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
RUN chmod +x ./kubectl
RUN mv ./kubectl /usr/local/bin/kubectl

# Install kube->aws
RUN curl -o aws-iam-authenticator https://amazon-eks.s3-us-west-2.amazonaws.com/1.13.7/2019-06-11/bin/linux/amd64/aws-iam-authenticator
RUN chmod +x ./aws-iam-authenticator
RUN mkdir -p $HOME/bin && cp ./aws-iam-authenticator $HOME/bin/aws-iam-authenticator && export PATH=$HOME/bin:$PATH
RUN echo 'export PATH=$HOME/bin:$PATH' >> ~/.bashrc

# Need to run more commands to configure:
# aws sts get-caller-identity
# aws eks --region us-east-2 update-kubeconfig --name k8s-demo-app-cluster

VOLUME /root/.aws/

# ENTRYPOINT ["/usr/local/bin/aws"]
ENTRYPOINT ["/bin/bash"]
