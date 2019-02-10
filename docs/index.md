# **私の研究**

2月のコンピューター研究です。

- Joaquin Menchaca (ジョアキーン•メンチャカ)

## **Areas of Study**

* Continious Integration • Continious Delivery
    * Build Tasks
    * Pipelines
        * GitOps
* Infrastructure
    * Iron Age (Bare Metal)
    * Cloud Age
        * Cloud Native Infrastructure
* Change Configuration
    * Desired State 
    * Immutable Production (deposble computing)

## **Topic Areas**

## **Desired State**

Here are some of my notes on these three tools that I have used professionally.

### **Puppet**

[Puppet](https://puppet.com/) uses a centralized Puppet Master server to managed desired state of client systems that have a puppet agent installed.  Change configuration code is written in propiertary DSL langauge called [manifests](https://puppet.com/docs/puppet/latest/lang_summary.html), and are packaged into components called [modules](https://puppet.com/docs/puppet/latests/modules.html).

[Puppet](https://puppet.com/) can use a site manifest to configure a list of systems based on host name, through a custom dynamic script (called [ENC](https://puppet.com/docs/puppet/latest/nodes_external.html)), or through a hierachical system of your choosing through [Hiera](https://puppet.com/docs/puppet/latest/hiera_intro.html).

[Puppet](https://puppet.com/) is well suited for *runtime change configuration* for static systems that do not change frequently.  For environments, where serives need to be configured as a set (clusters or microservices) or are more transitory (cloud or containers), Puppet's synchronous service discovery with [exported resources](https://puppet.com/docs/puppet/latest/lang_exported.html), does not scale well and becomes incredibly complex such coordination or orchestration scenario.

* [Puppet](https://puppet.com/)
* [Puppet Master](https://puppet.com/docs/puppetserver/latest/index.html)
* [Hiera](https://puppet.com/docs/puppet/latest/hiera_intro.html)

### **Chef**

[Chef](https://www.chef.io/chef/) uses a centralized Chef Server to managed desired state of client systems that have a chef-client agent installed.  Change configuration code is written in pseudo-DSL langauge using ruby and care called [recipes](https://docs.chef.io/recipes.html), which can be  packaged into components called [cookbooks](https://docs.chef.io/cookbooks.html).

[Chef](https://www.chef.io/chef/) is by far one of the more complex systems, as it requires three pieces: ① the chef server, ② the client configuration (called a node), and ③ a workstation to update changes to Chef Server and bootstrap nodes with the `knife` tool.  Chef has they own control system, similar to git, for chef objects, so there will be at least two sources of truth, what is in the git repository, and what is on the chef server.  These will need to be reconciled manually by human operator.

[Chef](https://www.chef.io/chef/) is well suited for *runtime change configuration* for static systems that do not change frequently.  For environments, where serives need to be configured as a set (clusters or microservices) or are more transitory (cloud or containers), Chef's synchronous service discovery with [chef search](https://docs.chef.io/chef_search.html), does not scale well and becomes incredibly complex such coordination or orchestration scenario.

* [Chef](https://www.chef.io/chef/)
* [Chef Server Components](https://docs.chef.io/server_components.html)
* [Chef Search](https://docs.chef.io/chef_search.html)

### **Ansible**

[Ansible](https://www.ansible.com/) is a deploy-orchestration tool that pushes configuration changes to a target host using scripts called [playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html) (DSL in YAML format), which can be packaged into components called [roles](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html).  Systems are categorized and configured through an [inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html), which can be a static list of hosts, or a [dynamic script](https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html) that generates a custom inventory on the fly.

[Ansible](https://www.ansible.com/) by itself does not manage desired state across systems, but this can be done through [Ansible Tower](https://www.ansible.com/products/tower), or open-source [AWX](https://www.ansible.com/products/awx-project).

[Ansible](https://www.ansible.com/) has been popular for custom deployment and orchestration solutions, especially when [Docker](https://www.docker.com) has released, but with popularity of Kubernetes, there is less of a need for this.

* [Ansible](https://www.ansible.com/)
* [Dynamic Inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html)
* [Ansible Tower](https://www.ansible.com/products/tower)

## **GitOps**

GitOps is a pattern were git is the source of truth, where branches, tags, and a pipeline DSL describes how and when software is released.  Inside the git repository, there will be build, configuration, and deployment scripts. 

In Kubernetes implementation, this could include Dockerfile for build, and Helm chart for deployment and *deploy time configuration* onto a Kubernetes cluster.

* **Concepts**
    * [​GitOps - Operations by Pull Request](https://www.weave.works/blog/gitops-operations-by-pull-request)
    * [GitOps: What you need to know](https://www.weave.works/technologies/gitops/)
    * [GitOps: Dev, with a Dash of Ops!](https://www.cloudbees.com/blog/gitops-dev-dash-ops)
* **Tools**
    * [Spinnaker](https://www.spinnaker.io/)
    * [Jenkins X](https://jenkins.io/projects/jenkins-x/)
    * [Flux](https://github.com/weaveworks/flux)

## **Cloud Native Infrastructure**

This book encapsulates a lot of the thought in this area:

* Cloud Native Infrastructure by Justin Garrison and Kris Nova: [https://www.cnibook.info/](https://www.cnibook.info/)