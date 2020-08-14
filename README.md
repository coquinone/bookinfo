# Bookinfo Sample

See <https://istio.io/docs/examples/bookinfo/>

## Build docker images without pushing

```bash
src/build-services.sh <version> <prefix>
```

Where `<version>` is the tag and `<prefix>` is the docker registry to tag the images.

For example: `src/build-services.sh 1.1.0 docker.io/istio`.

The bookinfo versions are different from Istio versions since the sample should work with any version of Istio.

## Update docker images in the yaml files

```bash
sed -i "s/\(istio\/examples-bookinfo-.*\):[[:digit:]]\.[[:digit:]]\.[[:digit:]]/<your docker image with tag>/g" */bookinfo*.yaml
```

## Push docker images to docker hub

One script to build the docker images, push them to docker hub and to update the yaml files

```bash
build_push_update_images.sh <version>
```

## Tests

Bookinfo is tested by istio.io integration tests. You can find them under [tests/examples](https://github.com/istio/istio.io/tree/master/tests/examples) in the [istio/istio.io](https://github.com/istio/istio.io) repository.

The reference productpage HTML files are in [tests/apps/bookinfo/output](https://github.com/istio/istio/tree/master/tests/apps/bookinfo/output). If the productpage HTML produced by the app is changed, remember to regenerate the reference HTML files and commit them with the same PR.
2020-08-12 20:32:46
2020-08-13 01:03:43
2020-08-14 19:28:26
2020-08-14 19:48:51
2020-08-14 20:07:47