# Load balanced vagrant setup with NGINX and PHP.
Please make sure vagrant is working fine.

### Getting started

```
vagrant up --provider=virtualbox to start server local server
ansible-playbook ansible/playbook.yml --inventory-file ansible/inventories/host
open http://192.168.56.93
```
