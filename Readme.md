# django-deployment.yaml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: django-app
  labels:
    app: django
spec:
  replicas: 3
  selector:
    matchLabels:
      app: django
  template:
    metadata:
      labels:
        app: django
    spec:
      containers:
        - image: ndrohith09/djangokubernetesproject81:latest
          name: django
          ports:
            - containerPort: 8001
              name: gunicorn
            
```

# django-svc.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: django
  labels:
    app: django
spec:
  type: NodePort
  selector:
    app: django
  ports:
    - port: 8001
      targetPort: 8001
```
