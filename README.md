squid_proxy
===========

This ansible role installs and configures squid proxy on the desired host. With this role you can set squid to allow networks or ip's defined by you, block access to the domains and so
restrict access based on the keywords.
The role also secures the squid proxy by enabling authentication, so no one without user and password can use it without permission. 


Role Variables
--------------

The role variables are defined in defaults/main.yml

      squid_port: the port on squid proxy will be listening
      local_net: a list of authorized network/s to access squid proxy
      squid_conf: squid proxy configuration path
      htpasswd_file: htpasswd file location to use for the authentication
      restricted_sites_file: file location of the domains to block
      restrict_keyword_file: file location of the keywords to block
      proxy_user: username to use to authenticate with squid proxy
      proxy_pass: proxy user password
      set_auth: [yes|no] to set role to also configure the authentication
      anonymize: [yes|no] to configure the traffic anonymization
      restrict_sites: [yes|no] to configure squid to block domains
      restrict_keywords: [yes|no] to configure squid to block traffic based on keywords
      allowed_ports: list of non ssl allowed ports 
      allowed_ssl_ports: list of ssl allowed ports 
      restricted_sites: block of restrticted domains
      restricted_keywords: block of restrticted keywords


Tags
-----

      configure_auth : this tag configures the authentication on squid proxy
      anonymize : this tag sets the squid configuration 
      restrict_sites : this tag configures the access blocking to the defined domains
      restrict_keywords : this tag configures the access blokcing based on keywords in the url's


Example Playbook
----------------

Example of playbook to use :

      - hosts: servers
	roles:
	  - { role: squid_proxy }

For the complete installation use  :

      ansible-playbook --connection=local --inventory 127.0.0.1, install_squid.yaml

To configure authentication on squid :

      ansible-playbook --connection=local --inventory 127.0.0.1, install_squid.yaml --tags configure_auth

To configure squid block the traffic to the defined domains:

      ansible-playbook --connection=local --inventory 127.0.0.1, install_squid.yaml --tags restrict_sites
    

Requirements
------------

      - ansible 2.7.7


Dependencies
------------

The following required packages are automatically installed be the ansible role on the remote host/s

      - httpd-tools
      - epel-release


License
-------

MIT

Author Information
------------------

	Raman Deep
	31th March 2020
	deep.raman85@gmail.com
