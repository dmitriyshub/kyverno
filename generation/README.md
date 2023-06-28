### Generation Policy
#### We will use a Kyverno generate policy to generate an image pull secret in a new Namespace.


- Create Object (for example pull-secret)
```
kubectl -n default create secret docker-registry regcred \
  --docker-server=myinternalreg.corp.com \
  --docker-username=john.doe \
  --docker-password=Passw0rd123! \
  --docker-email=john.doe@corp.com
```
- Create the policy 
- Create the namespace
```
kubectl create ns mytestns
```
- Check the new secret
```
kubectl -n mytestns get secret
```
- Delete the policy
```
kubectl delete clusterpolicy sync-secrets
```