# Ansible : Playbook Kibana

The aim of this project is to deploy Kibana on Vagrant instances.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to run this Ansible playbook :

*   [Vagrant](https://www.vagrantup.com/docs/installation/) must be installed on your computer
*   Update the Vagrant file based on your computer (CPU, memory), if needed
*   Update the operating system to deploy in the Vagrant file (default: Ubuntu)
*   An Elasticsearch cluster has to be deployed and accessible to fully deploy Kibana
*   Download the Ansible requirements:

```bash
$ ansible-galaxy install -r requirements.yml
```

### Usage

A good point with Vagrant is that you can create, update and destroy all architecture easily with some commands.

Be aware that you need to be in the Vagrant directory to be able to run the commands.

#### Baremetal Deployment

To deploy the Kibana client on baremetal, you have to configure the variable *kibana_install_type* to *baremetal* in the file kibana.yml before running the playbook :

```yaml
[...]
vars:
  kibana_install_type: baremetal
  kibana_elasticsearch_url: <CONFIGURE_IT>
[...]
```

Once it's done, you just have to provision the Vagrant instance and the Ansible playbook will automatically be called :

```bash
$ vagrant up
```

The Kibana Web interface should be accessible at : http://10.0.3.131:5601/

#### Docker Deployment

To deploy the Kibana client on Docker, you have to configure the variable *kibana_install_type* to *docker* in the file kibana.yml before running the playbook :

```yaml
[...]
vars:
  kibana_install_type: docker
  kibana_elasticsearch_url: <CONFIGURE_IT>
[...]
```

Once it's done, you just have to provision the Vagrant instance and the Ansible playbook will automatically be called :

```bash
$ vagrant up
```

If everything run has expected, you should have a Docker container named kibana.

The Kibana Web interface should be accessible at : http://10.0.3.131:5601/

#### Kubernetes Deployment

To deploy the Kibana client on Kubernetes, you have to configure the variable *kibana_install_type* to *kubernetes* in the file kibana.yml before running the playbook :

```yaml
[...]
vars:
  kibana_install_type: kubernetes
  kibana_elasticsearch_url: <CONFIGURE_IT>
[...]
```

Once it's done, you just have to provision the Vagrant instance and the Ansible playbook will automatically be called :

```bash
$ vagrant up
```

If everything run has expected, you should have a namespace and a pod named kibana. This pod should be configured by two config map kibana-config and kibana-pipeline.

The Kibana Web interface should be accessible at : http://10.0.3.131:5601/

#### Destroy

To destroy the Vagrant resources created, just run this command :

```bash
$ vagrant destroy
```

### How-To

This section list some simple command to use and manage the playbook and the Vagrant hosts.

#### Update with Ansible

To update the Kibana configuration with Ansible, you just have to run the Ansible playbook kibana.yml with this command :

```bash
$ ansible-playbook kibana.yml
```

#### Update with Vagrant

To update the Kibana configuration with Vagrant, you just have to run provisioning part of the Vagrant file :

```bash
$ vagrant provision
```

#### Connect to Vagrant instance

To be able to connect to a Vagrant instance, you should use the CLI which is configured to automatically use the default SSH key :

```bash
$ vagrant ssh kibana01
```

## Author

Member of Wikitops : https://www.wikitops.io/

## Licence

This project is licensed under the Apache License, Version 2.0. For the full text of the license, see the LICENSE file.
