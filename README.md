# Routereflector Monzo Build

This branch (MonzoImageBuild) is for building a custom monzo routereflector image. It *should* differ from the master branch only in `Makefile` changes.

Please don't ever merge this branch *back* into master. This way we can keep up to date with upstream if we need to.

We've made changes to the routereflector base image to move the location of `bird`/`bird6` controll sockets. There is currently a PR open at: [projectcalico](https://github.com/projectcalico/routereflector/pull/27) with all our changes

Once that PR is accepted we can set up a small entry in `monzo/docker-images` that simply retaggs the `calico/routereflector` image and uploads this to ECR

## Usage

(optionally update the MONZO_VERSION variable in the makefile)

1. Obtain an ECR login token for our build account: `aws ecr get-login --no-include-email --profile=build_admin`
2. Run the output of (1) in your shell to authenticate with ECR
3. `make build`
4. `make push`
