<div align="center">
<img src=https://static.wixstatic.com/media/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png/v1/fit/w_2500,h_1330,al_c/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png width="400" height="200">
 </div>

# <div align="center"> KUBERNETES DASHBOARD </p>

# <div align="center"> DevOps Instructor-led Training </div>

# <div align="right"> $`\textcolor{brown}{\text{Contact us: }}`$  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; </div>

<div align="right"> T O A C C E L E R A T E Y O U R C A R E E R G R O W T H </div>

### <div align="right"> For questions and more details: </div>

<div align="right"> <img src=https://w7.pngwing.com/pngs/759/922/png-transparent-telephone-logo-iphone-telephone-call-smartphone-phone-electronics-text-trademark-thumbnail.png width="20" height="20"> +91 98712 72900 </div>

<div align="right"> <img src=https://pbs.twimg.com/profile_images/1450734615946219520/jmBHQRRa_400x400.jpg width="20" height="20"> https://www.thecloudtrain.com </div>

<div align="right"> <img src=https://icons.iconarchive.com/icons/martz90/circle/512/email-icon.png width="20" height="20"> support@thecloudtrain.com </div>

<div align="right"> <img src=https://png.pngtree.com/png-vector/20221018/ourmid/pngtree-whatsapp-icon-png-image_6315990.png width="20" height="20"> +91 98712 72900 </div>

## INSTALLING KUBERNETES DASHBOARD

## _Steps for Master_

### Step 1: For installing Kubernetes Dashboard, run the following command:

`kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml`

![image](https://user-images.githubusercontent.com/37858762/236398622-b1e53026-fc48-4ed5-b9fd-25f817c8dc96.png)

### Step 2: Edit the Kubernetes Dashboard service with this command

`kubectl edit svc kubernetes-dashboard -n kubernetes-dashboard`

![image](https://user-images.githubusercontent.com/37858762/236333744-989d9562-0aad-4118-8e17-d145225c1af9.png)

### Step 3: Change the text **clusterip** to **nodeport**, once done save and exit.

![image](https://user-images.githubusercontent.com/37858762/236333695-a5f78172-06c3-48ff-aa67-f70617afb2d1.png)

### Step 4: Finally note down the IP address of the kubernetes-dashboard service using the following command:

`kubectl get svc kubernetes-dashboard -n kubernetes-dashboard`

![image](https://user-images.githubusercontent.com/37858762/236333678-4de69c17-4588-4a57-ad93-004ef0493abf.png)

### Step 5: Next browse, to the following address, to the see the login page of the dashboard:

https://\<ip-address-of-master-or-slave:\<nodeport\>

![image](https://user-images.githubusercontent.com/37858762/236333654-ec10bcb4-8e46-4641-820c-059537e63e34.png)

- 1. When you see *Your connection is not private...NET::ERR_CERT_INVALID* warning on Chrome,
- 2. Just type *thisisunsafe* and wait.

### Step 6: For login, use the following commands:

```
# Create service account
kubectl create serviceaccount cluster-admin-dashboard-sa
```
### Create a secret token for above service account using below file and save it with secret.yaml:

```
apiVersion: v1
kind: Secret
metadata:
  name: cluster-admin-dashboard-sa
  annotations:
    kubernetes.io/service-account.name: cluster-admin-dashboard-sa
type: kubernetes.io/service-account-token
```

```
# Bind ClusterAdmin role to the service account
kubectl create clusterrolebinding cluster-admin-dashboard-sa \
  --clusterrole=cluster-admin \
  --serviceaccount=default:cluster-admin-dashboard-sa

# Create the secret using above yaml file
kubectl apply -f secret.yaml

# Parse the token
TOKEN=$(kubectl describe secret $(kubectl -n kube-system get secret | awk '/^cluster-admin-dashboard-sa-token-/{print $1}') | awk '$1=="token:"{print $2}')
```

![image](https://user-images.githubusercontent.com/37858762/236333532-31dad5ac-e426-4983-a92d-6837a34962e1.png)

### Step 7: Now pass the following command, to view the token:

`echo $TOKEN`

![image](https://user-images.githubusercontent.com/37858762/236333523-dd1741dc-c480-45ab-8b26-40b866704e29.png)

### Step 8: Copy this token and paste it in the login page of Kubernetes Dashboard:

![image](https://user-images.githubusercontent.com/37858762/236333508-ee3f7a46-5082-430b-a53a-305fe4352c73.png)

![image](https://user-images.githubusercontent.com/37858762/236333490-3094c675-b13e-4bf7-b462-e1ae40f147c6.png)

Kubernetes Dashboard is now successfully installed!

