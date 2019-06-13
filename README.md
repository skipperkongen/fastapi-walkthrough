# FastAPI walkthrough

STATUS: Can't expose pod in minikube.

> https://fastapi.tiangolo.com/

> https://fastapi.tiangolo.com/deployment/

> https://kubernetes.io/docs/tutorials/hello-minikube/

```
pyenv local 3.7.3
pipenv install fastapi uvicorn
pipenv lock -r > requirements.txt
docker build -t skipperkongen/hello-fastapi:latest .
docker run -d -p 80:80 skipperkongen/hello-fastapi
# docker run -p 80:80 skipperkongen/hello-fastapi
curl http://localhost/items/42?q=yomomma
```

Kubernetes (local):

```
minicube start
kubectl create deployment hello-fastapi --image=docker.io/skipperkongen/hello-fastapi
kubectl expose deployment hello-fastapi --type=LoadBalancer --port=80
minikube stop
minikube delete
```
