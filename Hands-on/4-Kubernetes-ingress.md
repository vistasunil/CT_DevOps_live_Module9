<div align="center">
<img src=https://static.wixstatic.com/media/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png/v1/fit/w_2500,h_1330,al_c/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png width="400" height="200">
 </div>

# <div align="center"> KUBERNETES INGRESS </p>

# <div align="center"> DevOps Instructor-led Training </div>

<br />

<br />

<br />

<br />

# $${\color{brown} &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Contact&emsp;us: &emsp;&emsp;&emsp; }$$

<div align="right"> T O A C C E L E R A T E Y O U R C A R E E R G R O W T H </div>

### <div align="right"> For questions and more details: </div>

<div align="right"> <img src=https://w7.pngwing.com/pngs/759/922/png-transparent-telephone-logo-iphone-telephone-call-smartphone-phone-electronics-text-trademark-thumbnail.png width="20" height="20"> +91 98712 72900 </div>

<div align="right"> <img src=https://pbs.twimg.com/profile_images/1450734615946219520/jmBHQRRa_400x400.jpg width="20" height="20"> https://www.thecloudtrain.com </div>

<div align="right"> <img src=https://icons.iconarchive.com/icons/martz90/circle/512/email-icon.png width="20" height="20"> support@thecloudtrain.com </div>

<div align="right"> <img src=https://png.pngtree.com/png-vector/20221018/ourmid/pngtree-whatsapp-icon-png-image_6315990.png width="20" height="20"> +91 98712 72900 </div>

## CREATING AN INGRESS

## _Steps for Master_

### Step 1: We will first have to install an ingress controller 'nginx'. Execute the following command:

`kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.3.1/deploy/static/provider/baremetal/deploy.yaml`

![image](https://user-images.githubusercontent.com/37858762/236332123-b61ea671-2249-4621-9203-773ab37fbed7.png)

![image](https://user-images.githubusercontent.com/37858762/236332111-a3b72612-425f-47e2-85a5-3336d7675e85.png)

### Step 2: Next, since ingress routes to only cluster-ip services, let us delete our previously created nginx nodeport service and create a service with clusterip for nginx. Use the following commands:

`kubectl delete service nginx`

`kubectl create service clusterip nginx --tcp=80:80`

### Step 3: Next, we will have to create an ingress rule, create an ingress.yaml file with the below code:

```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ingress-nginx
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  ingressClassName: nginx
  rules:
    - http:
        paths:
          - path: /nginx
            pathType: Prefix
            backend:
              service:
                name: nginx-deployment
                port:
                  number: 80
```

### Step 4: Finally, create the ingress rule using the following command:

`kubectl create -f ingress.yaml`

If you face any error like below while deploying:

\<--validate=false Error from server (InternalError): error when creating "endpoint.yaml": Internal error occurred: failed calling webhook "validate.nginx.ingress.kubernetes.io": Post https://ingress-nginx-controller-admission.ingress-nginx.svc:443/extensions/v1beta1/ingresses?timeout=30s: context deadline\>

`kubectl delete -A ValidatingWebhookConfiguration ingress-nginx-admission`

Then run below command to fix and run create command again:

### Step 5: Let's verify if ingress is working or not, by checking the nodeport of the ingress service, for checking the nodeport use the following command:

`kubectl get svc -n ingress-nginx`

![image](https://user-images.githubusercontent.com/37858762/236332003-88afaa69-e94a-44a8-8181-d367d4400429.png)

### Step 6: Finally verify by browing to https://\<IP-address-of-master/slave\>:\<nodeport\>/nginx

![image](https://user-images.githubusercontent.com/37858762/236331987-3d51ae58-3174-4502-aa1e-48ef82464610.png)
