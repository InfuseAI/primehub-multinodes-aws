# Provision

The `cdk` module provides a docker image to launch aws-cdk that helps PrimeHub partners to create a multi-node sample.

## Usage

In order to make the cdk image working, you have to provide:

* the `$HOME/.aws` configuration
* arguments to create your own cluster
  * NAME is used in the node name
  * USERNAME is used in the resource tag
  * KEY\_NAME is the name of your key pair (not identity file name) used to `ssh` login. Please see [aws document](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html) for detail

Deploy
```bash
docker run --rm -it -v $HOME/.aws:/root/.aws:ro \
  -e NAME=demo -e USERNAME=demo -e KEY_NAME=demo_key \
  infuseai/cdk:v0.1 cdk deploy
```

Destroy
```bash
docker run --rm -it -v $HOME/.aws:/root/.aws:ro \
  -e NAME=demo -e USERNAME=demo -e KEY_NAME=demo_key \
  infuseai/cdk:v0.1 cdk destroy
```
