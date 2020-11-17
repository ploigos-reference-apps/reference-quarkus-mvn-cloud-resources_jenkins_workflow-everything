# reference-quarkus-mvn-cloud-resources (Jenkins) (Workflow: Standard)
The cloud resources for the [reference-quarkus-mvn_jenkins_workflow-standard](http://gitea.tssc.rht-set.com/ploigos-reference-applications/reference-quarkus-mvn_jenkins_workflow-standard) application.

## Install

### 0. Prerequisite

* TODO

### 1. Deploy Ploigos Kubernetes Resources

```bash
# this should be the namespace that Jenkins is running in
WORKFLOW_NAMESPACE=
helm dependency update charts/reference-quarkus-mvn-workflow

helm secrets upgrade --install \
    reference-quarkus-mvn-workflow ./charts/reference-quarkus-mvn-workflow \
    -f charts/reference-quarkus-mvn-workflow/values.yaml \
    -f charts/reference-quarkus-mvn-workflow/secrets.yaml \
    --namespace ${WORKFLOW_NAMESPACE} \
    --render-subchart-notes
```

### 2. Update Jenkinsfile

1. The helm chart run will have output `PGP Keys Secret: ${PGP_KEYS_SECRET}`, you need to update
the `pgpKeysSecretName` parameter in the Jenkinsfile in the associated project to this one
with that value.
2. TODO

### 2. Configure Jenkins

1. TODO
