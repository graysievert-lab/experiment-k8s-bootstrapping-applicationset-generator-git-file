# Experiment: Cluster bootstrapping using ArgoCD ApplicationSet and git:file generator

Assumption: Repo contains necessary charts and valuefiles, or valuefiles for charts in public Helm repos, or manifests.
Supposedly resonable for the cluster tooling repo.

Cons:

- configs in each directory
- each config contains links to this repository
- configs resemble application manifest too much
- Still ended up with helm-style go-templating

Pros:

- less copy pasting due to the reusage of fields equal to the basepath

NOTE:

to trigger webhook:

```shell
$ kubectl -n argocd port-forward services/argocd-applicationset-controller 7000:7000

$ curl -X POST localhost:7000/api/webhook \
-H 'Content-type: application/json' \
-H 'X-GitHub-Event: push' \
-d '{"ref": "HEAD","repository": {"ssh_url":"git@github.com:graysievert-lab/experiment-k8s-bootstrapping-applicationset-generator-git-file.git"}}'
```
