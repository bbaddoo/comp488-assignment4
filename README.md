Task 1.1:
Question: It doesn't have many permissions to enforce the principle of least privilege. The default service account can only create self subject review objects and get cluster endpoints. It can't read, list, or change anything such as the pods and deployments.

Task 1.2:
The error I got was: Error from server (Forbidden): pods is forbidden: User "system:serviceaccount:default:default" cannot list resource "pods" in API group "" in the namespace "default"

-The error is there because the service account in default does not have ny roles giving it permission to view or manage the Kubernetes resources. With the RBAC all of the actions are denied unless they are explicitly allowed.


Part 4: The mistakes are that the rolebinding is in the default namespace and there is a role mentioned in the production namespace. Rolebinding can only bind roles tht are in the same namespace. So, I moved rolebinding to the production namespace. Also, deployments go to the apps API group not the core one. So, I changed apiGroups to "apps".

