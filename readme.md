# Ansible AWS Certificate Manager

Creates AWS certificate requests. Allows for passing a validation domain. From the AWS [documentation](http://docs.aws.amazon.com/acm/latest/userguide/gs-acm-validate.html):

> To ensure that email is sent to the administrative addresses for an apex domain, such as example.com, rather than to the administrative addresses for a subdomain, such as test.example.com, specify the ValidationDomain option in the RequestCertificate API or the request-certificate AWS CLI command. This feature is not currently supported in the console.

Additionally, this role attempts to be idempotent by running `aws acm list-certificates` and ensuring that the domain of the cert being requested is not included in the current list of certificates.

## Example usage:

```
  roles:
    - role: ansible-acm
    acm_domain_name: secure.berrysmoke.com
    acm_validation_domain: berrysmoke.com

```
