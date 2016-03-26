# Parsoid Dockerfile - Ansible version

Builds a Parsoid Docker container image. This image is built using the [Ansible role](https://github.com/idi-ops/ansible-parsoid).

## Building

Build Ansible-provisioned image:
- `docker build --no-cache -t inclusivedesign/parsoid .`

## Testing

The container can be tested as part of a deployment by setting the *CONTAINER_TEST* environment variable to *true*.

The container will exit after the test and the exit code as a result of the run command can be used for further actions. The container can (to a certain extent) self-test using the development mode - see the run examples below - but this doesn't test the real production run-time configuration

### Run Examples

#### Run a container for production

```
docker run \
--name parsoid\
-d \
-p 8000:8000 \
-e PARSOID_DOMAINS="{ 'localhost': 'http://localhost/w/api.php' }" \
inclusivedesign/parsoid
```

#### Run a container in test mode

```
docker run \
--name parsoidtest \
-t \
--rm \
-e CONTAINER_TEST=true \
inclusivedesign/parsoid
```

