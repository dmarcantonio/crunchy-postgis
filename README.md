# Crunchy Postgis helm chart

A tested helm chart for Crunchy Postgis

## Charts

### Crunchy Postgis chart

A chart to deploy a high availability Crunchy Postgis cluster

#### Add chart to dependencies in your chart.yaml:

```
dependencies:
  - name: crunchy-postgis
    version: 0.5.0
    repository: https://dmarcantonio.github.io/crunchy-postgis/
```

#### Values are located in the documentation here:

[Crunchy Postgis Documentation](charts/crunchy-postgis/README.md)

### Crunchy Postgis tools chart

A set of standard service accounts and networking templates that were needed to deploy a Crunchy Postgis cluster but are kept separate from the main Crunchy Postgis chart.

#### Add chart to dependencies in your chart.yaml:

```
dependencies:
  - name: crunchy-postgres-tools
    version: 0.3.0
    repository: https://dmarcantonio.github.io/crunchy-postgis/
```

#### Values are located in the documentation here:

[Crunchy Postgres Tools Documentation](charts/tools/README.md)

## Release Process (WIP)

After you have made changes to a chart and are ready to release a new version you must bump the version in the `chart.yaml` file so the [chart releaser action](https://github.com/helm/chart-releaser-action) knows to publish a new version.

Once that is approved and merged you must tag and push the tag for the action to publish the release. The release workflow will automatically create a release for the updated chart as well as publish a separate release with an archive of the raw yaml files for those who don't want to use helm.

```
git checkout main
git tag -a crunchy-postgres-raw-yaml-v.0.2.0 -m "Release v0.2.0"
git push --tags
```

## Raw YAML files

An archive of the latest releases raw YAML files can be found in the [releases](https://github.com/dmarcantonio/crunchy-postgis/releases) section. These are bundled together unlike the Helm charts which are released separately.

Alternatively you can save them with the [helm template](https://helm.sh/docs/helm/helm_template/) command:

`helm template --output-dir yaml charts/crunchy-postgis`

`helm template --output-dir yaml charts/tools`

## Contact Info

[#crunchydb on Rocket.Chat](https://chat.developer.gov.bc.ca/channel/crunchydb)

## Vendor Info

[PGO, the Postgres Operator from Crunchy Data](https://access.crunchydata.com/documentation/postgres-operator/v5/)
