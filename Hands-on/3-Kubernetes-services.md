<div align="center">
<img src=https://static.wixstatic.com/media/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png/v1/fit/w_2500,h_1330,al_c/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png width="400" height="200">
 </div>

# <div align="center"> KUBERNETES SERVICEs </p>

# <div align="center"> DevOps Instructor-led Training </div>

# <div align="right"> $`\textcolor{brown}{\text{Contact us: }}`$  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; </div>

<div align="right"> T O A C C E L E R A T E Y O U R C A R E E R G R O W T H </div>

### <div align="right"> For questions and more details: </div>

<div align="right"> <img src=https://w7.pngwing.com/pngs/759/922/png-transparent-telephone-logo-iphone-telephone-call-smartphone-phone-electronics-text-trademark-thumbnail.png width="20" height="20"> +91 98712 72900 </div>

<div align="right"> <img src=https://pbs.twimg.com/profile_images/1450734615946219520/jmBHQRRa_400x400.jpg width="20" height="20"> https://www.thecloudtrain.com </div>

<div align="right"> <img src=https://icons.iconarchive.com/icons/martz90/circle/512/email-icon.png width="20" height="20"> support@thecloudtrain.com </div>

<div align="right"> <img src=https://png.pngtree.com/png-vector/20221018/ourmid/pngtree-whatsapp-icon-png-image_6315990.png width="20" height="20"> +91 98712 72900 </div>

## CREATING A SERVICE

## _Steps for Master_

### Step 1: We will create a nodeport service for our nginx deployment, run the following command:

`kubectl expose deployment nginx-deployment --type=NodePort --name=nginx`

![image](https://user-images.githubusercontent.com/37858762/236331161-ab9c2d19-05bf-47ec-add1-e884a39a4b96.png)

### Step 2: Note down the Nodeport for this service by running the command,

`kubectl get svc nginx`

![image](https://user-images.githubusercontent.com/37858762/236331180-c696c010-1a73-494c-90a0-a7a8db93a69d.png)

### Step 3: Verify the working of the service by browsing to the IP address of the master or slave with this port

![image](https://user-images.githubusercontent.com/37858762/236331193-aeb449de-63a5-426b-a2bb-c4b7c6a36fa4.png)
