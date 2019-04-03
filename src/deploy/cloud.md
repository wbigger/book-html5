# On-Premises
Aprire AWS Educate.
Lanciare un'istanza su AWS. Accedere via terminale.
```
sudo yum update

sudo yum install docker -y
sudo usermod -aG docker $USER
sudo systemctl start docker
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo yum install git -y
git clone https://github.com/marconicivitavecchia/my-project.git
```
Uscire con ctrl-D e rientrare
```
cd my-project
docker-compose up
```
Fatto!!!
