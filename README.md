# Managing my zones through OctoDNS

## Fetching from existing sources

```bash
# where schaakclublievegem.be. is the zone to dump the records in yaml format from
# where cloudflare is the source provider to pull from as specified in the config
octodns-dump --config-file .\config\production.yaml --output-dir zones schaakclublievegem.be. cloudflare
```

## Validating config / dry run

```bash
octodns-sync --config-file=./config/production.yaml
```

## Applying 

```bash
octodns-sync --config-file=./config/production.yaml --doit
```

## Provider configuration

The cloudflare_token needs to have the permission to edit all zones' records (Zone > DNS), additionally it requires the permission for Zone > Page Rules too.

## GH Action - automation

The automation makes use of the pre-configged automation over at https://github.com/octodns/octodns-docker.
Specifically the image octodns/cloudflare, if multiple flavors are required just use octodns/all.
