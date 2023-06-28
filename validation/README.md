### Validation Policy
#### Validation policy ensures a label called team is present on every Pod
#### Add the policy to your cluster. It contains a single validation rule that requires that all Pods have the team label. Kyverno supports different rule types to validate, mutate, generate, cleanup, and verify image configurations. The field validationFailureAction is set to Enforce to block Pods that are non-compliant. Using the default value Audit will report violations but not block requests

- Try creating a Deployment without the required label
```
kubectl create deployment nginx --image=nginx 
```
- You should see an error, In addition to the error returned, Kyverno also produces an Event in the same Namespace which contains this information.

- Now, create a Pod with the required label
```
kubectl run nginx --image nginx --labels team=backend
```

- Run the following command to retrieve the Policy Report that Kyverno just created.

```
kubectl get policyreport
```
 - If you were to describe the above policy report you would see more information about the policy and resource.

- clean up by deleting the policy you created above
```
kubectl delete clusterpolicy require-labels
```
