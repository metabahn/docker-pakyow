# docker-pakyow

Builds Docker containers for the [Pakyow](https://github.com/pakyow/pakyow) project, published nightly on [Docker Hub](https://hub.docker.com/u/pakyow).

## CI Containers

The following containers are intended for use in continuous integration environments.

* ci-ruby-2.5.7
* ci-ruby-2.5.8
* ci-ruby-2.6.5
* ci-ruby-2.6.6
* ci-ruby-2.7.0
* ci-ruby-2.7.1
* ci-ruby-2.7.2
* ci-ruby-head

Each container is build from the same [Dockerfile](https://github.com/metabahn/docker-pakyow/blob/84253cf27cd9a0314ee83297b3fa29ddd4d636a7/ci/Dockerfile), configured through build args.
