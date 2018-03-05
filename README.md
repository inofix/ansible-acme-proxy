[![Travis CI](https://img.shields.io/travis/inofix/ansible-acme-proxy.svg?style=flat)](http://travis-ci.org/inofix/ansible-acme-proxy)


Acme-Tiny Install
=================

This is an ansible role for transfering the certificate between a host that organizes the signing with Let's Encrypt and the (this) host which hosts the service (mail, jabber, what ever..). This role is to be run on the service side, getting the certificates from the remote end where the signing was requested.

Why we do not use one of the existing roles?

* For the first reason read the section "Promise" below. We need something reliable.
* This role will be used by [maestro](https://github.com/inofix/maestro) and must follow the logic used there. (Of course, the role can be used without maestro..)


State
-----

preSTABLE (Feature-Freeze/RC)


Promise
-------

Sure, this role may change in the future, but we will only expand features to not break backwards compatibility.

If radical changes should become necessary, a new role will be created, probably with an 'ng' or version suffix...


Installation
------------

 # ansible-galaxy install inofix.acme-proxy


Requirements
------------

* Ansible >2.0
* Python2/3 on target host
* Generic UNIX with FHS


Role Variables
--------------

* app\_\_acme\_\_home - optional, default='/var/lib/acme'
* app\_\_acme\_\_config\_dir - optional, default='/etc/ssl/acme'
* app\_\_acme\_\_scripts\_dir - optional, default='/etc/ssl/acme/scripts'
* app\_\_acme\_\_bin\_dir - optional, default='/usr/local/bin'
* app\_\_acme\_\_domain - optional, default=[ {domain='example.com'} ]
* app\_\_acme\_\_letsencrypt\_certs - optional, default=[ {url='https://letsencrypt.org/certs/lets-encrypt-x3-cross-signed.pem', file='intermediate.crt'}, {url='https://letsencrypt.org/certs/isrgrootx1.pem', file='ca.crt'} ]
* app\_\_acme\_\_cron\_minute - optional, default='55'
* app\_\_acme\_\_cron\_hour - optional, default='4'
* app\_\_acme\_\_cron\_day - optional, default='\*'
* app\_\_acme\_\_cron\_month - optional, default='\*'
* app\_\_acme\_\_cron\_year - optional, default='\*'
* fqdn - optional, default={{ ansible\_fqdn | d(inventory\_hostname ) }}

Dependencies
------------

* inofix.acme-request
 * (inofix.acme-setup)


Example Playbook
----------------

    - hosts: servers
      roles:
         - inofix.acme-proxy

(See inofix.acme-setup)

License
-------

GPLv3


Author Information
------------------

* Michael Lustenberger at [inofix.ch](http://www.inofix.ch)
