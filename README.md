[![Travis CI](https://img.shields.io/travis/inofix/ansible-acme-cron-proxy.svg?style=flat)](http://travis-ci.org/inofix/ansible-acme-cron-proxy)


Acme-Tiny Install
=================

This is an ansible role for transfering the certificate between a host that organizes the signing with Let's Encrypt and the (this) host which hosts the service (mail, jabber, what ever..). This role is to be run on the service side, getting the certificates from the remote end where the signing was requested.

Why we do not use one of the existing roles?

* For the first reason read the section "Promise" below. We need something reliable.
* This role will be used by [maestro](https://github.com/inofix/maestro) and must follow the logic used there. (Of course, the role can be used without maestro..)


State
-----

UNSTABLE!


Promise
-------

Sure, this role may change in the future, but we will only expand features to not break backwards compatibility.

If radical changes should become necessary, a new role will be created, probably with an 'ng' or version suffix...


Installation
------------

 # ansible-galaxy install inofix.acme-cron-proxy


Requirements
------------

* Ansible >2.0
* Python2/3 on target host
* Generic UNIX with FHS


Role Variables
--------------

* app\_\_acme\_\_remote\_proxy - mandatory, hostname of where to find the certificates to collect


Dependencies
------------

* inofix.acme-setup


Example Playbook
----------------

    - hosts: servers
      roles:
         - inofix.acme-cron-proxy

License
-------

GPLv3


Author Information
------------------

* Michael Lustenberger at [inofix.ch](http://www.inofix.ch)
