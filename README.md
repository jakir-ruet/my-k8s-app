# Getting Started with Create my-k8s-app

```bash
npm start
npm test
npm run build
npm run eject
```

Create docker repository

```bash
jakirbd/my-k8s-app
```
Create Dockerfile & write following lines
```bash
FROM node:20
WORKDIR /my-app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["npm", "start"]
```
Run the command
```bash
docker build -t jakirbd/my-k8s-app:01 . # where 01 is version tag
docker login
docker push jakirbd/my-k8s-app:01
```

Create, Run & deployment
```bash
kubectl create deployment my-react-k8s-app --image=jakirbd/my-k8s-app:01
kubectl get deployments
kubectl get pods
kubectl logs my-react-k8s-app-557ff5d95-xkr8f
kubectl expose deployment my-react-k8s-app --port=3000 --type=LoadBalancer
kubectl get services
minikube service my-react-k8s-app
```