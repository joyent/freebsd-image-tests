# Overview

These are the tests used to validate FreeBSD KVM images before being released to the images.joyent.com and the Joyent Public Cloud.

These tests are are based on [Serverspec](http://serverspec.org).

This test suite is used in conjunction with [mi-freebsd-10](https://github.com/joyent/mi-freebsd-10)

## Installation and Setup

To run the tests you will need ruby (1.9.3+ or 2.0.0 should work) and rubygems installed.

Install serverspec with

`gem install serverspec`

Add the name and attibutes of what you want to test to attributes.yml. Next, edit your `~/.ssh/config` file with the host information of the virtual machines you want to test. The name you chose for _Host_ in `~/.ssh/config should match what you have in attributes.yml. 

For example, here's a attrubutes.yml file:

```
freebsd-10:
  :roles:
    - freebsd
  :name: FreeBSD 10
  :base_version: 20141105
  :doc_url: http://wiki.joyent.com/jpc2/Freebsd
```

And an example `~/.ssh/config` file:

```
freebsd-10 
  HostName XX.X.XXX.XXX
  User root
```

## Running the tests

To run the tests, run the following command (within this directory):

```
rake serverspec
```

More information on how to create serverspec tests can be found here:

http://serverspec.org/tutorial.html

There's a list of useful Resource Types here that you can use for testing:

http://serverspec.org/resource_types.html
