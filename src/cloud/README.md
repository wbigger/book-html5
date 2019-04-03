
- https://hackernoon.com/running-docker-on-aws-ec2-83a14b780c56
```
systemctl start
sudo yum update -y
sudo yum install -y docker
sudo usermod -aG docker ec2-user # logout per avere effetto
```

- https://docs.docker.com/compose/install/
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

docker-compose --version
```

- installare git:
```
sudo yum install -y git
```

- lanciare docker:
```
sudo systemctl start docker
```
