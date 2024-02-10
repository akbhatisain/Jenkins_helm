###https://github.com/omerbsezer/Fast-Kubernetes/blob/main/K8s-Helm-Jenkins.md

edit values in  value.yml:

persistence:
   enabled: false   ##(if true)


servicetype: NodePort  ##(if clusterIP)

jenkins default username or password:

  admin:
    username: "admin"
    password: "admin"
