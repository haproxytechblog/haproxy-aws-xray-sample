# HAProxy AWS X-Ray for Distributed Tracing

Use AWS X-Ray for distributed tracing with HAProxy.

## Usage

Add the file **haproxy-xray/credentials** and add the AWS access key and secret access key, such as:

```
[default]
aws_access_key_id = AKIAIQ...
aws_secret_access_key = NLWyU0...
```

Change the AWS region where AWS X-Ray is running if needed in [haproxy-xray/Dockerfile](https://github.com/haproxytechblog/haproxy-aws-xray-sample/blob/master/haproxy-xray/Dockerfile).

Start the demo by using `docker-compose up`:

```
docker-compose up -d
```

Then, monitor the *haproxy* or *xray* container logs.

```
docker-compose logs -f xray
```

To get a full example running, log into the [AWS Console](https://console.aws.amazon.com/) and go to the AWS X-Ray *Getting Started* tab. From there, you can launch a sample Node.js application that comes equipped to send X-Ray segments. Then, replace the `server` address in **haproxy.cfg** with the public IP of the sample application. This will be shown as the *ElasticBeanstalkEnvironmentURL* on the *Outputs* tab on the CloudFormation *Stacks* screen.