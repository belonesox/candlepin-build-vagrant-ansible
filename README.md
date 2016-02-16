# candlepin-build-vagrant-ansible
Building development version of candlepin with ansible (and possible Vagrant)

Some automation to deploy developer version of CandlePin over minimal Centos 7 installation.
http://www.candlepinproject.org/docs/candlepin/developer_deployment.html

Ansible playbooks (can be used without vagrant) and Vagrant file for full automation.

Just run «vagrant up» and you will have latest candlepin on 
with 
* localhost:22 — SSH
* localhost:6443  — Candlepin port
* localhost:6432  — Postgres




Optionally install «vagrant plugin install vagrant-hosts».
