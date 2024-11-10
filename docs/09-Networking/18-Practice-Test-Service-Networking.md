# Practice Test Service Networking

  - Take me to [Practice Test](https://kodekloud.com/topic/practice-test-service-networking/)

#### Solution 

1. <details>
   <summary>What network range are the nodes in the cluster part of?</summary>

   ```
   kubectl get nodes -o wide
   ```

   Note the INTERNAL-IP column to derive:

   ```
   192.20.116.0/24
   ```
   </details>

2. <details>
   <summary>What is the range of IP addresses configured for PODs on this cluster?</summary>

   ```
   kubectl get pods -A -o wide
   ```

   From this list, exclude the static control plane pods like `kube-apiserver` as these run on the host network, not the pod network. From the remaining pods we can derive:

   ```
   10.244.0.0/16
   ```

   OR
   ```
   k logs weave-net-vcmcj -n kube-system | grep "ipalloc-range"
   ```
   </details>

3. <details>
   <summary>What is the IP Range configured for the services within the cluster?</summary>

   ```
   kubectl get service -A
   ```

   Note the CLUSTER-IP column to derive:

   ```
   10.96.0.0/12
   ```

   OR

   ```
   cat /etc/kubernetes/manifests/kube-apiserver.yaml   | grep cluster-ip-range
   ```

   OR
   ```
   ps aux | grep kube-api | grep  --color cluster-ip-range
   ```
   ![image](https://github.com/user-attachments/assets/cdc8b39f-29f9-4c9c-b120-f03593877b19)

   </details>

4. <details>
   <summary>How many kube-proxy pods are deployed in this cluster?</summary>

   ```
   kubectl get pod -n kube-system | grep kube-proxy
   ```

   Count the results
   </details>

5. <details>
   <summary>What type of proxy is the kube-proxy configured to use?</summary>

   From the output of the above question, you have two kube-proxy pods, e.g.

   ```
   controlplane ~ kubectl get pod -n kube-system | grep kube-proxy
   kube-proxy-rtr8p                       1/1     Running   0             56m
   kube-proxy-t7w8f                       1/1     Running   0             56m
   ```

   Pick either and check its logs. The answer is there.

   ```
   k logs -n kube-system kube-proxy-rtr8p
   ```

   OR

   Check logs at /var/log/pods/kube-system_kube-proxy*/kube-proxy/0.log
   ![image](https://github.com/user-attachments/assets/7b3bbade-7afb-47ff-ba0b-be17612ab434)

   </details>

7. <details>
   <summary>How does this Kubernetes cluster ensure that a kube-proxy pod runs on all nodes in the cluster?</summary>

   ```
   kubectl get all -n kube-system
   ```

   From this, you can see that `kube-proxy` is a `daemonset`
   </details>

