# CNI in Kubernetes

  - Take me to [Lecture](https://kodekloud.com/topic/cni-in-kubernetes/)

In this section, we will take a look at **Container Networking Interface (CNI) in Kubernetes**
![image](https://github.com/user-attachments/assets/2b7f1bcb-e4fa-411e-9176-e194d1419eb1)

## Configuring CNI

![image](https://github.com/user-attachments/assets/2c060db2-7528-4e6a-96ff-7bd742aaa165)


![net-1](../../images/net1.PNG)


- Check the status of the Kubelet Service

```
$ systemctl status kubelet.service
```

## View Kubelet Options

```
$ ps -aux | grep kubelet
```

## Check the Supportable Plugins 

- To check the all supportable plugins available in the `/opt/cni/bin` directory.

```
$ ls /opt/cni/bin

```

## Check the CNI Plugins

- To check the cni plugins which kubelet needs to be used.

```
ls /etc/cni/net.d

```
![image](https://github.com/user-attachments/assets/ef50bcaf-44fd-4d25-961a-73e7c0c927d5)

## Format of Configuration File  

![net-2](../../images/net2.PNG)


#### References Docs

- https://kubernetes.io/docs/reference/command-line-tools-reference/kubelet/
- https://kubernetes.io/docs/concepts/extend-kubernetes/compute-storage-net/network-plugins/
