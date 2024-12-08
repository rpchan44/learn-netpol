## K8s network policy 101

In Kubernetes, a NetworkPolicy is an object that allows you to define rules to control the communication (ingress and egress) between pods and/or namespaces within a Kubernetes cluster. These policies enable you to secure network traffic and implement fine-grained access control between different services and components of your application.

<b>Key Features of NetworkPolicy:</b>
Control Traffic Flow: NetworkPolicies allow you to define which pods can communicate with each other. By default, all pods in Kubernetes can communicate with each other, but with a NetworkPolicy in place, you can restrict traffic based on specific rules.

Isolation: You can isolate groups of pods from each other. For example, you could create a NetworkPolicy that only allows certain pods to access a database or API, and block all other communication.

<b>Granular Control:</b> NetworkPolicies can be applied based on:

<b>Pod labels:</b> You can apply policies to pods that match certain labels.
Namespaces: Policies can be enforced across namespaces.
<b>IP ranges:</b> You can specify IP blocks (CIDR ranges) from which traffic can originate.
<b>Port numbers:</b> You can define which ports should be open for ingress or egress traffic.

<b>Ingress and Egress Traffic:</b>

Ingress: Controls incoming traffic to pods.
Egress: Controls outgoing traffic from pods.

<b>How NetworkPolicy Works:</b>
Pod Selector: You define which pods the policy applies to by selecting them based on labels. For instance, you can apply a policy to a set of frontend application pods or backend services.

Allow or Deny Traffic: By default, without a NetworkPolicy, all pods are allowed to communicate with each other. When you define a NetworkPolicy, you can specify which sources (other pods, IP ranges, etc.) are allowed to send traffic to the selected pods, and which ports they can use.

<b>Policy Types:</b>

Ingress: Specifies rules for incoming traffic to selected pods.
Egress: Specifies rules for outgoing traffic from selected pods.
If no policy is defined, the default is to allow all traffic.


# In this demo the geist is basically like this

In frontend tier only pods with role loadbalancer can hit its ingress port 80 / nginx
In the backend tier only pods with role frontend-tier can hit its ingress port 80 / nginx
In the db tier only the pods with role backend-tier can hit hit its ingress port 3306 / mysql 