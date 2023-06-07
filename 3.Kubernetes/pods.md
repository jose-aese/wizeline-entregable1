Pods Corriendo 

<img width="539" alt="image" src="https://github.com/jose-aese/wizeline-entregable1/assets/45864492/2b221c15-3b90-47ce-9950-983e55490e59">

<img width="1028" alt="image" src="https://github.com/jose-aese/wizeline-entregable1/assets/45864492/f663886f-16c4-4840-9473-5be21c42bba1">


Comando 

kubectl create -f deployMongo.yml

Codigo 

apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongodb-deployment
  labels:
    app: mongodb
spec:
  replicas: 2
  selector:
    matchLabels:
      app: mongodb
  template:
    metadata:
      labels:
        app: mongodb
    spec:
      containers:
      - name: mongodb
        image: mongo
        ports:
        - containerPort: 27017
---
apiVersion: v1
kind: Service
metadata:
  name: mongodb-service
spec:
  selector:
    app: mongodb
  ports:
    - protocol: TCP
      port: 27017
      targetPort: 27017
