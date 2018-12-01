# helm-cleanup

This [helm chart](https://helm.sh/) allows specifying a [time to live](https://en.wikipedia.org/wiki/Time_to_live) (TTL) for its own [helm release](https://docs.helm.sh/glossary/#release).

This is a utility chart, meaning that it is meant to be installed only as a dependency of a parent chart.

For information on adding dependencies to your chart, see: https://docs.helm.sh/developing_charts/#chart-dependencies.

## Example Usage

This example demonstrates installation of `mychart`, which should be built with a dependency on the cleanup chart.

```cli
helm install [mychart] \
  --set cleanup.timeToLive.enabled=true \
  --set cleanup.timeToLive.duration=8h
```

For a toy example, we can install the cleanup chart directly with a short TTL and observe that it deletes its own release within about 60 seconds:

```cli
helm install . \
  --set timeToLive.enabled=true \
  --set timeToLive.duration=60s
```
