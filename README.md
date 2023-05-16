# ansible-acme-demo

Example how to use Ansible module `community.crypto.acme_certificate`.

This example asumes that playbook is executed on system where HTTP server is runnig and that user executing it has permisons to write into `acme_web_dir`, see source.

Example:
```
ansible-playbook -e acme_domain=microsoft.com -e acme_force=true playbook.yml
```

This will try to create certificate with cn=microsoft.com and subjAltNames=['microsoft.com', 'www.microsoft.com'] and it will fail during challenge creation with error `The ACME server refuses to issue a certificate for this domain name, because it is forbidden by policy`. Try to use hostname of system you are executing playbook on.
