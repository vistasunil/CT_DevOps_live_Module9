<div align="center">
<img src=https://static.wixstatic.com/media/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png/v1/fit/w_2500,h_1330,al_c/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png width="400" height="200">
 </div>

# <div align="center"> KUBERNETES ASSIGNMENT </p>

# <div align="center"> DevOps Instructor-led Training </div>

# <div align="right"> $`\textcolor{brown}{\text{Contact us: }}`$  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; </div>

<div align="right"> T O A C C E L E R A T E Y O U R C A R E E R G R O W T H </div>

### <div align="right"> For questions and more details: </div>

<div align="right"> <img src=https://w7.pngwing.com/pngs/759/922/png-transparent-telephone-logo-iphone-telephone-call-smartphone-phone-electronics-text-trademark-thumbnail.png width="20" height="20"> +91 98712 72900 </div>

<div align="right"> <img src=https://pbs.twimg.com/profile_images/1450734615946219520/jmBHQRRa_400x400.jpg width="20" height="20"> https://www.thecloudtrain.com </div>

<div align="right"> <img src=https://icons.iconarchive.com/icons/martz90/circle/512/email-icon.png width="20" height="20"> support@thecloudtrain.com </div>

<div align="right"> <img src=https://png.pngtree.com/png-vector/20221018/ourmid/pngtree-whatsapp-icon-png-image_6315990.png width="20" height="20"> +91 98712 72900 </div>

#
</br>

## $`\textcolor{red}{\text{NOTE: USE UBUNTU 22.04 VIRTUAL MACHINES FOR ALL THE LABS}}`$

## Exercise 1: Kubernetes Deployment and NodePort Service

### Complete below tasks as part of this exercise:

* Create a Kubernetes deployment file to deploy 3 replicas of apache pods
* Now expose this deployment using NodePort service
* Access this deployment on web browser using NodePort IP and Port

## Exercise 2: Kubernetes ClusterIP Service and Ingress

### Complete below tasks as part of this exercise:

* Use the previous deployment and make it accessible using Ingress
* Delete the existing NodePort service and create a ClusterIP service in place of it
* Now, create an Ingress object that will route the traffic to this service and hence deployment using two paths as below. Both should map to same backend service and port:
  * /app
  * /apache

_**Note: Make sure that Ingress Controller is installed to make ingress work.**_

* Access this deployment on web browser using Ingress Controller's IP

## Exercise 3: Case Study

**You have just joined a start-up company as a Devops Lead Engineer. The company relies on a Monolithic Architecture for its product. Recently, the senior management was hired. The new CTO insists on having a Microservice Architecture. The Development Team is working on breaking the Monolith. Meanwhile, you have been asked to host a Test Application on Kubernetes, to understand how it works.**

### Following things have to be implemented:

* Deploy an Apache2 deployment of 2 replicas. This is your deployment1
* Use the sample code at Git-Hub repo: https://github.com/vistasunil/devopsIQ.git.
* You have to clone and containerize this code, and push it to DockerHub. Once done, deploy it on Kubernetes with 2 replicas. This is your deployment2
* Create two ClusterIPs services for each deployment
* Deploy Ingress with the following rules pointing to respective service:
  * /apache should point to the apache pods using its service as backend
  * /kapp should point to the github application pods using its service as backend
