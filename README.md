To deploy:

1) Add the IP to the hosts file so it looks like

[wordpress]
192.168.1.1 ansible_user=root...

2) Update variable in the vars section of openvpn_based.yaml

  vars:
    domain: <domain of the website to be host>
    site_prefix: <the name of the site for the purposes of file names like the apache configuration file>

Variables with defaults include
  base_www_dir - The base directory of Apache, default /var/www
  site_prefix: Described above, default is wordpress
  apache_dir: The location of the Apache config files, default /etc/apache2
  max_upload: The maximum file upload size to use in php.ini, default 256M
  max_post: The maximum post file size to use in php.ini, default 256M
  fresh_install: If this is the first install of any website and apache2/mysql need to be installed, default: true
  remove_default: Whether or not the default Apache site should be removed, default: true

3) Install requirements

ansible-galaxy install -r requirements.yaml

4) Run the playbook

ansible-playbook wordpress.yaml
