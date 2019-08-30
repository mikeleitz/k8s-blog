# Overview

This directory helps you deploy these examples out to your AWS eks (Kubernetes) account.

You can create a Docker image that has the relevant AWS commands.  I find this easier than configuring your laptop to do it, since I'm always bouncing back and forth between different Kubernetes implementations: the rPi cluster, Google, Amazon, and IBM.

# AWS

## Build the image

Here's the Docker commands to get your image built.

```bash
docker build -t aws .
```

## Enter the image

```bash
docker run --rm -e  AWS_ACCESS_KEY_ID=<YOUR KEY> -e "AWS_SECRET_ACCESS_KEY=YOUR" -ti aws ecr get-login --no-include-email --region <YOUR REGION>
```

### References

 * [how-to-install-aws-cli-in-docker-container-based-on-image-python2-7](https://stackoverflow.com/questions/51923207/how-to-install-aws-cli-in-docker-container-based-on-image-python2-7)
