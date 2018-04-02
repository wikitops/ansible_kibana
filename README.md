# Ansible : Playbook Kibana
The aim of this project is to deploy a Kibana client on Vagrant with or without Docker (with by default).

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to run this Ansible playbook :

* [Vagrant](https://www.vagrantup.com/docs/installation/) must be installed on your computer
* Update the Vagrant file based on your computer (CPU, memory), if needed
* You must have download the ubuntu Xenial64 vagrant box :

```
vagrant box add https://app.vagrantup.com/ubuntu/boxes/xenial64
```
* Choose your deployment type (Docker or package) by setting the variable dockerised to true or false
* You must have a running Elasticsearch cluster
* Before running the playbook, you must configure the variable kibana_elasticsearch_url with the right URL to one of your Elasticsearch nodes

### Usage

A good point with Vagrant is that you can create, update and destroy all architecture easily with some commands.

Be aware that you need to be in the Vagrant directory to be able to run the commands.

#### Build Environment

Vagrant needs to init the project to run and build it :

```
vagrant up
```

After build, you can check which virtual machine Vagrant has created :

```
vagrant status
```

If all run like it is expected, you should see something like this :

```
$ vagrant status

Current machine states:

kibana01                  running (virtualbox)
```

#### Deployment

To deploy the Kibana client, you just have to run the Ansible playbook kibana.yml with this command :

```
ansible-playbook kibana.yml
```

If everything run has expected, you should access to Kibana : http://10.0.3.131/

#### Destroy

To destroy on what Vagrant has created, just run this command :

```
vagrant destroy
```

## Author

Member of Wikitops : https://www.wikitops.io/
