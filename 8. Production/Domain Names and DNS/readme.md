From this [slack convo](https://andela.slack.com/archives/C2VGBPMU7/p1495452543489183?thread_ts=1495447245.530355&cid=C2VGBPMU7): 

- Map new domain to an IP in the dns manager
- Map new domain to a service in kubernetes ingress.

Note that we are not using NGINX but google cloud l7 loadbalancer.
Written into an [ingress file](https://github.com/andela/micro-deployment-scripts/blob/develop/environments/ingress/prod/ingress.yaml)

```
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: entrypoint
spec:
  tls:
  - secretName: tls-secret
  backend:
    serviceName: default-http-backend
    servicePort: 80
  rules:
  - host: skilltree.andela.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: skilltree-svc
          servicePort: 50050
  - host: pulse.andela.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: pulse-front-svc
          servicePort: 50050
  - host: kaizen.andela.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: kaizen-svc
          servicePort: 50050
  - host: admin.andela.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: admin-svc
          servicePort: 50050
  - host: allocations.andela.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: allocations-svc
          servicePort: 50050
  - host: fis.andela.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: fis-svc
          servicePort: 50050
  - host: portal.andela.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: portal-svc
          servicePort: 50050
  - host: candela.andela.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: candela-svc
          servicePort: 50050
  - host: vof.andela.com
    http:
      paths:
      - path: /*
        backend:
          serviceName: vof-svc
          servicePort: 50050
```