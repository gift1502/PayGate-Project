Option 2: Question

DevOps Assessment: Mpho Masekwameng

Solution for Option 2

Hello, World application code with NodeJS

const express = require('express')
const app = express()
const port = 3000
app.get('/', (req, res) => res.send(Hello World!'))
app.listen(port, () => console.log('Example app listen on port ${port}!'))


DockerFile( for our NodeJS Hello World app)

FROM Node:latest
WORKDIR /app
ADD . .
RUN npm install
CMD node index.js


Building an image from My Dockerfile
docker build --tag hello-world:latest .


Running a container from my image
docker run --name hello-world -d -p 3000:3000 hello-world:latest


Pushing my image to dockerhub
docker push hello-world:latest


Load balancing the application with Minikube

Hello-world deployment.yaml

apiversion:app/v1
kind:Deployment
metadata:
  name:hello-world
spec:
  selector:
    matchlabels:
      app:hello-world
      
replicas:5 # tell the deployment to run 5 pods matching the template
template:
  metadata:
    labels:
      app:hello-world
  spec:
    containers:
    image:hellow-world
    ports:
  - containerPort:80
  
  Kubectl apply –f hello-world deployment.yaml
  
  
  Hellow-world service.yaml
  
  apiversion:v1
kind:service
metadata:
  name:ms-service-loadbalancer
spec:
  type:loadBalancer
  selector:
    app:hello-world-api
  ports:
-protocol:TCP
 port:3200
 targetPort:3000
 nodePort:30010
 
 Kubectl apply –f hellow-world service.yaml
 
 
Kubectl get pod
Kubectl get deployment
Kubectl get service


Thanks
Mpho Masekwameng


