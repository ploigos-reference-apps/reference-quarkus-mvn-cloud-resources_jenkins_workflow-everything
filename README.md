# reference-quarkus-mvn-cloud-resources (Jenkins) (Workflow: Everything)
The cloud resources for the [reference-quarkus-mvn (everything)](https://gitlab.apps.tssc.rht-set.com/ploigos-reference-applications/everything/reference-quarkus-mvn
application when using Jenkins and the Everything workflow.

## Install

### 0. Prerequisite

* TODO

### 1. Deploy Ploigos Kubernetes Resources

```bash
# this should be the namespace that Jenkins is running in
WORKFLOW_NAMESPACE=
helm dependency update charts/reference-quarkus-mvn-workflow

helm secrets upgrade --install \
    reference-quarkus-mvn-workflow-eve ./charts/reference-quarkus-mvn-workflow \
    -f charts/reference-quarkus-mvn-workflow/values.yaml \
    -f charts/reference-quarkus-mvn-workflow/secrets.yaml \
    --namespace ${WORKFLOW_NAMESPACE} \
    --render-subchart-notes
```

### 2. Update GitLab CI Script

1. The helm chart run will have output `PGP Keys Secret: ${PGP_KEYS_SECRET}`, you need to update
the `pgpKeysSecretName` parameter in the .gitlab-ci.yml in the associated project to this one with
that value.
2. TODO

### 2. Configure Jenkins

1. TODO
