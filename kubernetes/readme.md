# Kubernetes mock environment

A vagrant VM that runs both Kubernetes master and one Kubernetes node.

Credentials: `vagrant:a`

## Usage

Start the VM

```
sudo vagrant up
```

<sup>Run `gpasswd -a ${USER} libvirt` to add your user to 'libvrit' group to avoid necessity to run vagrant commands as root.</sup>

Get VM's console

```
sudo vagrant ssh
```

Run demo container in three replicas accessible from outside (type inside the VM)

```
kubectl run nginx --image=nginx --replicas=3
kubectl expose deployment nginx --type=LoadBalancer --port=80
# display the ip address of nginx
kubectl get services
# access the service
curl <nginx-ip-address>
```

Shutdown the VM

```
sudo vagrant halt
```