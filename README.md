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
