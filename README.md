# ansible-acme-demo

Example how to use Ansible module `community.crypto.acme_certificate`.

This example asumes that playbook is executed on system where HTTP server is runnig and that user executing it has permisons to write into `acme_web_dir`, see source.

Example:
```
ansible-playbook -e acme_domain=www.microsoft.com -e acme_force=true playbook.yml
```
