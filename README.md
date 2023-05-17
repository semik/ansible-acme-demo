# ansible-acme-demo

Example how to use Ansible module `community.crypto.acme_certificate`.

This example asumes that playbook is executed on system where HTTP server is runnig and that user executing it has permisons to write into `acme_web_dir`, see source.

## Example with Let's Encrypt
```
ansible-playbook -e acme_domain=microsoft.com -e @vars/lets-encrypt-staging.yml -e acme_account_email=email@example.com playbook.yml
```
This will try to create certificate with `cn=microsoft.com` and `subjAltNames=['microsoft.com', 'www.microsoft.com']` and it will fail during challenge creation with error `The ACME server refuses to issue a certificate for this domain name, because it is forbidden by policy`.

Try it with hostname of system you are executing playbook on, if you are running HTTP server.

## Example with ZeroSSL
```
ansible-playbook -e @vars/zero-ssl.yml -e acme_domain=microsoft.com -e acme_account_email=email@example.com playbook.yml
```

If you want to use ZeroSSL you need to sign-up there first, than create file `vars/zero-ssl.private` with content:
```
kid: 
key: 
alg: HS256
```
and put there `key id` and `key` from developer section on ZeroSSL.
