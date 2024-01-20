# ddclient chart

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: ddclient-secret
  labels:
    app: ddclient
stringData:
  ddclient.conf: |
    daemon=300
    syslog=yes
    protocol=cloudflare
    zone=meowsergirl.com
    use=web
    web=https://domains.google.com/checkip
    ssl=yes
    ttl=1
    login=you@gmail.com
    password=apitoken
    home.meowsergirl.com

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ddclient-deployment
  labels:
    app: ddclient
spec:
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 1
  replicas: 1
  selector:
    matchLabels:
      app: ddclient
  template:
    metadata:
      labels:
        app: ddclient
    spec:
      volumes:
        - name: ddclient-config-file
          secret:
            secretName: ddclient-secret
      containers:
        - name: ddclient
          image: linuxserver/ddclient
          imagePullPolicy: Always
          volumeMounts:
            - mountPath: /config
              name: ddclient-config-file
          resources:
            requests:
              cpu: 10m
              memory: 64Mi
            limits:
              cpu: 50m
              memory: 128Mi

```

Reference: <https://kubesail.com/template/loopDelicious/ddclient>