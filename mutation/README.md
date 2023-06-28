### Mutation Policy
#### This policy will add the label team to any new Pod and give it the value of bravo but only if a Pod does not already have this label assigned. Kyverno has the ability to perform basic “if-then” logical decisions in a very easy way making policies trivial to write and read. The +(team) notation uses a Kyverno anchor to define the behavior Kyverno should take if the label key is not found.

- Create the policy
- Create a pod
```
kubectl run redis --image redis
```
- get the Pod to see if the team label was added
```
kubectl get pod redis --show-labels
```
- Create a Pod, this time one which does already define the team label.
```
kubectl run newredis --image redis -l team=alpha
```
- Check once again for labels
```
kubectl get pod myredis --show-labels
```
- Clean up by deleting the policy you created
```
kubectl delete clusterpolicy add-labels
```