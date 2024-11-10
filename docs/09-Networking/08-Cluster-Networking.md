# Pre-requisite Cluster Networking

  - Take me to [Lecture](https://kodekloud.com/topic/cluster-networking/)

In this section, we will take a look at **Pre-requisite of the Cluster Networking**

- Set the unique hostname.
- Get the IP addr of the system (master and worker node).
![image](https://github.com/user-attachments/assets/4d48521a-5c65-4ab1-ba90-4d1c515f0508)

- Check the Ports.
  - Master and Worker
    ![image](https://github.com/user-attachments/assets/805bd58e-3638-4aee-9f5a-589c14dd9eb2)
  - Multiple masters
    ![image](https://github.com/user-attachments/assets/0c4abdf8-aa01-44c9-9fbd-59fc0d6b3aa6)



## IP and Hostname

- To view the hostname

```
$ hostname 
```

- To view the IP addr of the system

```
$ ip a
```


## Set the hostname

```
$ hostnamectl set-hostname <host-name>

$ exec bash
```

## View the Listening Ports of the system

```
$ netstat -nltp
```


![image](https://github.com/user-attachments/assets/0ec612e5-33b8-4c7e-a7a4-2482b806a13a)

#### References Docs

- https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/#check-required-ports
- https://kubernetes.io/docs/concepts/cluster-administration/networking/
