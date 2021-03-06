# Welcome!!

WARNING: Intrigue is currently in ALPHA. If you need assistance, please join us in #intrigue on irc.freenode.net.

Intrigue-core is a framework for attack surface discovery. 

<img src="https://raw.githubusercontent.com/intrigueio/intrigue-core/develop/doc/home.png" width="700">

To get started, follow the instructions below!

### Setting up a development environment

Follow the appropriate setup guide:

 * Docker (preferred) - https://intrigue.io/2017/03/07/using-intrigue-core-with-docker/
 * Ubuntu Linux - https://github.com/intrigueio/intrigue-core/wiki/Setting-up-a-Test-Environment-on-Ubuntu-Linux
 * Kali Linux - https://github.com/intrigueio/intrigue-core/wiki/Setting-up-a-Test-Environment-on-Kali-Linux
 * OS X - https://github.com/intrigueio/intrigue-core/wiki/Setting-up-a-Test-Environment-on-OSX-10.10

Now that you have a working environment, browse to the web interface.

### Using the web interface

To use the web interface, browse to http://127.0.0.1:7777

Getting started is pretty straightforward, follow this guide: https://intrigue.io/2017/03/07/using-intrigue-core-with-docker/

### Configuring modules

Many modules require API keys. To set them up, browse to the "Configure" tab and click on the name of the module. You will be taken to the relevant signup page where you can provision an API key.

### API usage via core-cli:

A command line utility has been added for convenience, core-cli.

List all available tasks:
```
$ bundle exec ./core-cli.rb list
```

Start a task:
```
$ bundle exec ./core-cli.rb start dns_lookup_forward DnsRecord#intrigue.io
```

Start a task with options:
```
$ bundle exec ./core-cli.rb start dns_brute_sub DnsRecord#intrigue.io resolver=8.8.8.8#brute_list=1,2,3,4,www#use_permutations=true
[+] Starting task
... <snip>
```

### API usage via curl:

You can use the tried and true curl utility to request a task run. Specify the task type, specify an entity, and the appropriate options:

```
$ curl -s -X POST -H "Content-Type: application/json" -d '{ "task": "example", "entity": { "type": "String", "attributes": { "name": "8.8.8.8" } }, "options": {} }' http://127.0.0.1:7777/v1/task_runs
```

### Ruby gem for the API:
[![Gem Version](https://badge.fury.io/rb/intrigue_api_client.svg)](http://badge.fury.io/rb/intrigue_api_client)
