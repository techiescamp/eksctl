# eksctl
AWS EKS example cluster configurations using eksctl

#Requirment

1. Cluster with multi az
2. Pod networking enabled
3. Node labelling 
4. Ingress 
5. Serive type loadbalancers
6. Deploy app with SSL

Others:

1. Kubernetes dashboard
2. vault integration
3. AWS secret integartion
4. IAM service accounts


## Command Referenceeks

Create Cluster:

<pre>eksctl create cluster -f eks-spot.yaml</pre>

List Cluster:

<pre>

eksctl get clusters 

</pre>

## Manage Node Groups

<pre>
ksctl delete nodegroup --cluster eks-spot-cluster ng1-public

eksctl create nodegroup -f eks-spot.yaml

eksctl create nodegroup --config-file=eks-spot.yaml --include='ng-spot' --exclude='ng1-public'

<pre>

## IAM
<pre>
aws sts get-caller-identity

mapUsers: |
  - userarn: arn:aws:iam::790307344871:user/scriptcamp
    username: scriptcamp
    groups:
    - system:bootstrappers
    - system:nodes
</pre>

## Kubeconfig:

Update kubeconfig

<pre>
aws eks update-kubeconfig --region us-west-2 --name eks-spot-cluster
</pre>