# elasticsearch
This repo is a fork of Logsearch that removes the rest of the ELK stack - Logstash and Kibana - in favor of a simple Elasticsearch cluster.


This release is based on Elasticsearch 2.x


## Getting Started

This repo contains Logsearch Core; which deploys an ELK cluster that can recieve and parse logs via syslog
that contain JSON.

Most users will want to combine Logsearch Core with a Logsearch Addon to customise their cluster for a
particular type of logs.  Its likely you want to be following an Addon installation guides - see below
for a list of the common Addons:

  * [Logsearch for CloudFoundry](https://github.com/logsearch/logsearch-for-cloudfoundry)

If you are sure you want install just Logsearch Core, read on...

## Installing Logsearch Core

0. Clone and upload

        $ git clone
        $ git submodule update --init --recursive
        $ bosh upload release https://bosh.io/d/github.com/logsearch/logsearch-boshrelease

0. Customise your deployment stub:

   * Make a copy of `templates/stub.$INFRASTRUCTURE.example.yml` to `logsearch-stub.yml`
   * Edit to match your IAAS settings

0. Generate a manifest

        $ scripts/generate_deployment_manifest $INFRASTRUCTURE logsearch-stub.yml > elasticsearch.yml

0. Deploy!

    $ bosh -d elasticsearch.yml deploy


## License

[Apache License 2.0](./LICENSE)
