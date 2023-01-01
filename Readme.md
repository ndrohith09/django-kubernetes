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

# results

![image](https://user-images.githubusercontent.com/73429989/210174660-177cdf8f-4837-434c-bd50-119ee4478569.png)

![image](https://user-images.githubusercontent.com/73429989/210174688-5d378daa-2a20-4b75-b45f-0c6d799e4084.png)

![image](https://user-images.githubusercontent.com/73429989/210174703-3723fae5-c0a9-4572-8ba1-348480e8ff1d.png)

