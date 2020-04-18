# Ansible: 3-node Elasticsearch cluster and Kibana

This repository includes an Ansible playbook to install and configure a 3-node Elasticsearch cluster and Kibana server in a suitable environment. The cluster is suitable to run in a local non-production or development environment such as a local vagrant deployment - like this one: [Vagrant: 3-node Elasticsearch cluster and Kibana Server](https://github.com/ethanhillas/vagrant-3-node-elasticsearch-kibana).

This ansible playbook is set up to use the vagrant deployment [here](https://github.com/ethanhillas/vagrant-3-node-elasticsearch-kibana). It uses the default vagrant user and defualt insecure private key, so **is only suited for local deployments**.

The playbook installs and cofigures Elasticsearch 7.6.2 on all hosts listed under the es_hosts group in the inventory file. Kibana 7.x is installed and configured on all hosts listed under the kibana_hosts group.

To get started with this playbook:
1. Download this repository to your local machine and ensure ansible (>2.0) is installed.
2. Configure your inventory file to reflect the infrastructure you have set up. Elasticsearch nodes should be listed under the es_hosts group and Kibana servers should be listed under the kibana_hosts group.
3. (Optional) If you want to connect to the hosts with a different user than `vagrant` or the default vagrant private key ensure this is set up by changing the ansible_user and ansible_ssh_private_key_file variables in the inventory file.
4. Install the ansible roles for Elasticsearch and Kibana:
    * Elasticsearch role (Official role from [Elastic](https://github.com/elastic/ansible-elasticsearch)): Run `ansible-galaxy install elastic.elasticsearch`
    * Kibana role (Role from [geerlingguy](https://github.com/geerlingguy/ansible-role-kibana)): `ansible-galaxy install geerlingguy.kibana`
5. Finally, to install Elasticsearch and Kibana, run `ansible-playbook -i inventory elastic_stack.yml`