Demo Cluster
============

SETUP
-------

1. Created Route53 zone vovayartsev.dyn.tixey.fom
2. Registered wildcard certificate
3. Created Cluster with KOPS
4. Installed HELM (helm init)
5. Configured ssl arn:xxxxx:xxxxx and installed democluster chart (usually Newrelic and elastic.co configurations go into “cluster” chart too)
6. MANUALLY created wildcard record in DNS (not used route53-mapper b/o additional IAM permissions)

OPERATIONS
----------

1. Specified values in values.yaml for demoapp chart
2. Installed demoapp chart into —namespace=feature-123 under —name=feature-123
3. Installed demoapp chart into —namespace=feature-456 under —name=feature-456


OPINIONS
---------

PROS OF APPROACH
- [ ] HTTPS redirects out of the box
- [ ] Ingress settings live in demoapp,
- [ ] Revisions are hard-coded in values.yaml and can be pushed between environments

PROS OF ELB
- [ ] No need to track SSL expiry (even Microsoft is guilty of this)
- [ ] Min config, max security (fixing outdated TLS algorithms / Heartbleed etc)

PROS OF KOPS
- [ ] 10x more stars in Github
- [ ] blessed by AWS

IDEAS
- [ ] https://github.com/sorenmat/k8s-rds (Beta)
