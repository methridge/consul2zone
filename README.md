# Consul to BIND Zone

[Consul Template](https://github.com/hashicorp/consul-template) to read all
services registered in [Consul](https://www.consul.io/) and create a
[BIND](https://www.isc.org/bind/) zone file.

## Usage

The `dns.tmpl` file is the base for your zone file. Include your SOA
information, NS, MX and other static records for your zone.

The template uses the unix timestamp as the serial number so you get automatic
incrementing.

Update the `template.hcl` file to include your Consul ACL token, if needed. And
if desired a post-exec command or script validate your zone file and reload
bind.

Once ready this can be run via the following command, with debug logging

```shell
consul-template -config=template.hcl -log-level=debug
```
