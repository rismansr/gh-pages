# Kubernetes

## Pod & Container Introspection

| Command                                    | Function                                        |
| ------------------------------------------ | ----------------------------------------------- |
| `kubectl get pods`                         | List the current pods                           |
| `kubectl describe pod <name>`              | Describe pod (name)                             |
| `kubectl get rc`                           | List the replication controllers                |
| `kubectl get rc --namespace="<namespace>"` | List the replication controllers in (namespace) |
| `kubectl describe rc <name>`               | Describe replication controller (name)          |
| `kubectl describe svc <name>`              | Describe service (name)                         |
| `kubectl delete pod <name>`                | Delete pod (name)                               |
| `kubectl get nodes –w`                     | Watch nodes continuously                        |

## Cluster Introspection

| Command                        | Function                        |
| ------------------------------ | ------------------------------- |
| `kubectl version`              | Get version information         |
| `kubectl cluster-info`         | Get cluster information         |
| `kubectl confg view`           | Get the confguration            |
| `kubectl describe node <node>` | Output information about a node |

## Debugging

- Execute 'command' on 'service' optonally # selectng container <$container>

`kubectl exec <service> <command> [-c <$container>]`

- Get logs from service 'name' optonally # selectng container <$container>

`kubectl logs -f <name> [-c <$container>]`

- Watch the Kubelet logs

`watch -n 2 cat /var/log/kublet.log`

- Show metrics for nodes

`kubectl top node`

- Show metrics for pods

`kubectl top pod`

## Quick Command

- Launch a pod called 'name' using image 'image-name'

`kubectl run <name> --image=<image-name>`

- Create a service described in 'manifest.yaml'

`kubectl create -f <manifest.yaml>`

- Scale replication controller 'name' to 'count' instances

`kubectl scale --replicas=<count> rc <name>`

- Map port 'external' to port 'internal' on replication controller 'name'

`kubectl expose rc <name> --port=<external> --targetport=<internal>`

- Stop all pods on 'n'

`kubectl drain <n> --delete-local-data --force --ignoredaemonsets`

- Create namespace 'name'

`kubectl create namespace <namespace>`

- Allow Kubernetes master nodes to run pods

`kubectl taint nodes --all node-role.kubernetes.io/master-`

## Objects

all
clusterrolebindings
clusterroles
cm = confgmaps
controllerrevisions
crd = customresourcedefnition
cronjobs
cs = componentstatuses
csr = certifcatesigningrequests
deploy = deployments
ds = daemonsets
ep = endpoints
ev = events
hpa = horizontalpodautoscalers
ing = ingresses
jobs
limits = limitranges
netpol = networkpolicies
no = nodes
ns = namespaces
pdb = poddisruptionbudgets
po = pods
podpreset
podtemplates
psp = podsecuritypolicies
pv = persistentvolumes
pvc = persistentvolumeclaims
quota = resourcequotas
rc = replicationcontrollers
rolebindings
roles
rs = replicasets
sa = serviceaccounts
sc = storageclasses
secrets
sts = statefulsets