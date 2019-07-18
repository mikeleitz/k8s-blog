# Overview


# k8s-demo-app example

In the 01_k8s-demo-app-kubernetes_deployment.yaml manifest, k8s will deploy the sample application located in my [k8s-demo-app Github repository](https://github.com/mikeleitz/k8s-demo-app-springboot).
 
You can access a few different endpoints of this application.  

| url                   | purpose                                            |
|-----------------------|----------------------------------------------------|
| 192.168.2.10/hostname | Return the hostname the application is running on. |
| 192.168.2.10/guid     | Return an id value.                                |

# MySQL example

In the 02_mysql-kubernetes_deployment.yaml manifest, it starts a MySQL database but it doesn't persist the data over restarts or if the pod moves.

This is a simple example, and later we'll add persistent storage via NFS mounts or similar scalable storage. 

## mycli

Use the mycli client to connect (or whatever client you want).  Change the ip address to the master node as appropriate.

The username/password is root/mysql.

```bash
mycli -u root -p -h mysql://192.168.2.10:3306
```
