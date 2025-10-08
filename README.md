# Installing AAP on OpenShift

## Deploy Operator
```console
01-aap-namespace.yaml
02-aap-operatorgroup.yaml
03-aap-subscription.yaml
```

## Create a secret for no reason
- https://github.com/ansible/awx-operator/issues/1751
```console
oc create secret -n aap docker-registry redhat-operators-pull-secret \
  --docker-server=dummy.example.com \
  --docker-username=dummy \
  --docker-password=dummy
```

## Create admin pass secret
oc create -f admin-password-secret.yaml

## Create Object bucket claim
oc create -f object-bucket-claim.yaml

oc get secret galaxy-bucket-claim
oc get cm galaxy-bucket-claim

## Create secret with S3 creds? or get it?

## Get Route
```console
oc get routes -n ansible-automation-platform
```
oc get secret/<your instance name>-<admin_user>-password -o yaml
oc get secret/example-admin-password -o yaml
oc get secret/example-admin-password -o jsonpath={.data.password} | base64 --decode



