Title: Cert Manager for Kubernetes
Date: 1/21/2021 10:00 PM
Author: L.J. Hanson
Tags: kubernetes, ssl, docker
Slug: Cert-Manager

Overall installtion instructions are [here](https://cert-manager.io/docs/installation/kubernetes/).  Cert Manager was installed by Helm v3, with the custom resource definitions (CRD).

ClusterIssuer.yaml file sets up the connection to the CA (Let's Encrypt) in order to generate certs.
\- Requires an IAM policy for Route53 and DNS challenges
\- yaml file must be updated with approriate values (at a minimum role, possibly accessKey and secret)
