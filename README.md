1. create an EC2 instance t2-micro type and a key pair
2. login to EC2 instance by 
```
ssh -i <key-pair> hostname@<ip-address>
```
3. Clone the git using git clone <repo-url>
4. create dockerfile Dockerfile in frontend app directory
```
FROM node:14
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
CMD ["npm","start"]
```
5. give permission for the current user to run docker without sudo
```
sudo chown $USER /var/run/docker.sock
```
6. Build the image
```
docker build -t three-tier-frontend .
```
7. Run the image 
```
docker run -d -p <hostport>:<container-port> -t three-tier-frontend
```
Check the running containers
```
$ docker ps
CONTAINER ID   IMAGE                        COMMAND                  CREATED         STATUS         PORTS                                       NAMES
1302bfd65102   three-tier-frontend:latest   "docker-entrypoint.s…"   8 minutes ago   Up 8 minutes   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp   beautiful_mcclintock
sunkara@sunkara-VivoBo
```
