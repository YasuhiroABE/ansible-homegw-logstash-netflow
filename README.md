YasuhiroABE.homegw-logstash-netflow
=========

This role sets up logstash and java deb packages for home router.
The logstash is used for collecting the netflow packet-header information.

Requirements
------------

This role is tested on the following platforms.

### Ansible
- Version 2.4

### Distributions
- Ubuntu 16.04

Role Variables
--------------

### Default
    ## hostname of logstash running node
    logstash_hostname: localhost
    
	## If you accept the oracle java license, please turn it to "true".
	logstash_accept_oracle_license_v1_1: "false"
    
    ## local file path of the logstash deb package
	## Please download the debpackage from the following location.
	## https://www.elastic.co/jp/downloads/logstash
	logstash_deb_srcpath: files/logstash-6.0.0.deb

	## the destination path of the logstash deb package
	logstash_deb_destpath: /tmp/logstash.deb
	logstash_deb_fileperm:
	  owner: root
	  group: root
	  mode: '0644'

	## netflow configuration filepath on the remote system
	logstash_conf_netflow_filepath: /etc/logstash/conf.d/netflow.conf
	logstash_conf_netflow_fileperm:
	  owner: root
	  group: root
	  mode: '0644'

	## destination ip address of the elasticsearch host
	logstash_conf_netflow_dest_ip: 192.168.0.1

	## destination port number of the elasticsearch host
	logstash_conf_netflow_dest_port: 9200

Dependencies
------------

N/A

Example Playbook
----------------

    - hosts: all
	  vars:
	    logstash_hostname: "server1"
	    logstash_accept_oracle_license_v1_1: "true"
		logstash_deb_srcpath: "files/logstash-6.2.2.deb"
      roles:
        - YasuhiroABE.homegw-logstash-netflow

License
-------

Apache License 2.0

Author Information
------------------

[Yasuhiro ABE](http://www.yasundial.org/foaf.xml)
