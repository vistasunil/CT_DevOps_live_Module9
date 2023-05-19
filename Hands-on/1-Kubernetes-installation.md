<div align="center">
<img src=https://static.wixstatic.com/media/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png/v1/fit/w_2500,h_1330,al_c/1c706c_a5df0ad56f894928bf858a74ba744b32~mv2.png width="400" height="200">
 </div>

# <div align="center"> KUBERNETES INSTALLATION </p>

# <div align="center"> DevOps Instructor-led Training </div>

# <div align="right"> $`\textcolor{brown}{\text{Contact us: }}`$  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; </div>

<div align="right"> T O A C C E L E R A T E Y O U R C A R E E R G R O W T H </div>

### <div align="right"> For questions and more details: </div>

<div align="right"> <img src=https://w7.pngwing.com/pngs/759/922/png-transparent-telephone-logo-iphone-telephone-call-smartphone-phone-electronics-text-trademark-thumbnail.png width="20" height="20"> +91 98712 72900 </div>

<div align="right"> <img src=https://pbs.twimg.com/profile_images/1450734615946219520/jmBHQRRa_400x400.jpg width="20" height="20"> https://www.thecloudtrain.com </div>

<div align="right"> <img src=https://icons.iconarchive.com/icons/martz90/circle/512/email-icon.png width="20" height="20"> support@thecloudtrain.com </div>

<div align="right"> <img src=https://png.pngtree.com/png-vector/20221018/ourmid/pngtree-whatsapp-icon-png-image_6315990.png width="20" height="20"> +91 98712 72900 </div>

## INSTALLING KUBERNETES

## _Steps for Both Master and Slave_

_**Note: Install container runtime on both master and slave following below link:**_

[**Docker official installation page for ubuntu**](https://docs.docker.com/engine/install/ubuntu/)

_**This will install docker and containerd both. Kubernetes is going to use containerd for cluster, as docker is not supported from 1.23 version onwards.**_

### Step 1: Run the following commands for installing kubeadm and other components as root:

```
echo '{"exec-opts": ["native.cgroupdriver=systemd"]}' >> /etc/docker/daemon.json
systemctl daemon-reload && systemctl restart docker.service
apt-get update && apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -

cat << EOF >/etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF

apt-get update
apt install -y kubeadm=1.24.1-00 kubelet=1.24.1-00 kubectl=1.24.1-00

# use below command to check kubectl and kubeadm versions
kubectl version --client
kubeadm version
```

## _Steps for Kubernetes Master_

### Step 1: Initialize kubeadm using the following command:

`kubeadm init --apiserver-advertise-address=<control-plane-ip> --pod-network-cidr=192.168.0.0/16 --ignore-preflight-errors=NumCPU --kubernetes-version 1.24.0`

![image](https://user-images.githubusercontent.com/37858762/236329634-6ab0e61d-9b2d-40fe-9795-d1d2467c7fc9.png)

![image](https://user-images.githubusercontent.com/37858762/236329650-7e0734f0-92de-4dbf-b30d-47aee1882bd0.png)

### Step 2: In the output of the previous command, you will get a command, take this command and run it in the slave

![image](https://user-images.githubusercontent.com/37858762/236329676-42421c73-8afa-4a93-968b-98343cbd42d2.png)

### Step 3: On the master, exit to the normal user, and execute the following commands:

```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

![image](https://user-images.githubusercontent.com/37858762/236329750-ef0d3114-ce34-4745-8d53-f793f2496bb0.png)

### Step 4: Next, let's install the network plugin. Execute the following commands:

```
kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/tigera-operator.yaml
kubectl create -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/custom-resources.yaml
```

### Step 5: The previous command will take some time to take effect. After 4-5 mins, try the following command, if both the nodes are in the ready state, Installation is successful!

`kubectl get nodes`

![image](https://user-images.githubusercontent.com/37858762/236329783-bd96c5b1-e2ca-4149-8b9a-960d97dc5c52.png)
