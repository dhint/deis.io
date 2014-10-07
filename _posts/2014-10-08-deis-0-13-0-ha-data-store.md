---
layout: post
title: "Deis v0.13 - Highly Available Data Storage"
author: carmstrong
meta:
  - name: description
    content: Deis' data is now stored safely with Ceph
  - name: keywords
    content: deis, release, 0.13, ceph, highly-available
---

The Deis project is happy to bring you the [v0.13.0 release](https://github.com/deis/deis/releases/tag/v0.13.0).

<!--more-->

If you are coming from an earlier version of Deis, read the ["Upgrading Deis"](http://docs.deis.io/en/latest/installing_deis/upgrading-deis/) documentation for details.

## What is Deis?

Deis is an open source PaaS that makes it easy to deploy and manage applications on your own servers. Deis builds upon [Docker](http://docker.io/) and [CoreOS](https://coreos.com/) to provide a lightweight PaaS with a Heroku-inspired workflow.

## 0.13.0 Summary

### New Features

- **store** is a new [Ceph](http://ceph.com)-backed component used to store persistent data
- **database** now stores backups and ships WAL logs to **store**
- **registry** now stores layers in **store**
- The **logspout** service on each CoreOS host removes the need for sidecar logging containers
- The **publisher** service on each CoreOS host removes the need for sidecar announce containers
- `deis` command-line client can be installed with `curl -sSL http://deis.io/deis-cli/install.sh | sh`
- A specific version of `deis` can now be installed with `curl -sSL http://deis.io/deis-cli/install.sh | sh -s 0.13.0`
- A specific version of `deisctl` can now be installed with 'curl -sSL http://deis.io/deisctl/install.sh | sh -s 0.13.0`

### Under the Hood

- Updated to [CoreOS 459.0.0](https://coreos.com/releases/#459.0.0)
- Updated to [fleet v0.8.3](https://github.com/coreos/fleet/releases/tag/v0.8.3)
- All Dockerfiles are now based on Ubuntu 14.04
- All data containers except logger-data are no longer necessary and have been removed
- CoreOS installs get deisctl on provision
- Move the `deisctl` project to deis/deis

### Merged Pull Requests

- ref(builder/registry): have builder push slugrunner in ExecStartPost - [#2062](https://github.com/deis/deis/pull/2062) ([@gabrtv](https://github.com/gabrtv))
- Retry Fleet container scheduling operations - [#2072](https://github.com/deis/deis/pull/2072) ([@gabrtv](https://github.com/gabrtv))
- fix(deisctl): bump default etcd timeout to 10s - [#2074](https://github.com/deis/deis/pull/2074) ([@carmstrong](https://github.com/carmstrong))
- fix(deisctl): bump status pollwait sleeps to 3s - [#2071](https://github.com/deis/deis/pull/2071) ([@carmstrong](https://github.com/carmstrong))
- docs(ec2): move "scale routers" section after platform installation - [#2070](https://github.com/deis/deis/pull/2070) ([@mboersma](https://github.com/mboersma))
- docs(managing_deis): remove dead machine from etcd cluster - [#2068](https://github.com/deis/deis/pull/2068) ([@carmstrong](https://github.com/carmstrong))
- fix(deisctl): don't set SSH tunnel for refresh-units command - [#2067](https://github.com/deis/deis/pull/2067) ([@mboersma](https://github.com/mboersma))
- docs(managing_deis): link to Ceph troubleshooting guide - [#2065](https://github.com/deis/deis/pull/2065) ([@carmstrong](https://github.com/carmstrong))
- feat(router): Changed store hostname to deis-store - [#2054](https://github.com/deis/deis/pull/2054) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- docs(standards): remove [skip ci] instructions - [#2016](https://github.com/deis/deis/pull/2016) ([@Joshua-Anderson](https://github.com/Joshua-Anderson))
- docs(releases): update procedure for Deis releases - [#2050](https://github.com/deis/deis/pull/2050) ([@mboersma](https://github.com/mboersma))
- fix(publisher): skip when failed to retrieve container - [#2053](https://github.com/deis/deis/pull/2053) ([@bacongobbler](https://github.com/bacongobbler))
- docs(*): doc changes based on store - [#1994](https://github.com/deis/deis/pull/1994) ([@carmstrong](https://github.com/carmstrong))
- feat(store): add deis-store component - [#1910](https://github.com/deis/deis/pull/1910) ([@carmstrong](https://github.com/carmstrong))
- feat(client): "make installer" creates distributable CLI package - [#2045](https://github.com/deis/deis/pull/2045) ([@mboersma](https://github.com/mboersma))
- feat(logspout): introduce deis/logspout - [#1992](https://github.com/deis/deis/pull/1992) ([@bacongobbler](https://github.com/bacongobbler))
- chore(*): bump CoreOS to 459.0.0 - [#2029](https://github.com/deis/deis/pull/2029) ([@carmstrong](https://github.com/carmstrong))
- fix(deisctl): fix global unit display - [#2039](https://github.com/deis/deis/pull/2039) ([@gabrtv](https://github.com/gabrtv))
- ref(builder): replace python with bash - [#1859](https://github.com/deis/deis/pull/1859) ([@bacongobbler](https://github.com/bacongobbler))
- fix(deisctl): refresh-units uses $HOME/.deis/units by default - [#2034](https://github.com/deis/deis/pull/2034) ([@mboersma](https://github.com/mboersma))
- fix(router): Use official javascript content type - [#2040](https://github.com/deis/deis/pull/2040) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- fix(tests): Increased test timeout for smoke tests - [#2043](https://github.com/deis/deis/pull/2043) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- fix(router): update to confd 0.5.x branch to fix sort issue - [#2033](https://github.com/deis/deis/pull/2033) ([@gabrtv](https://github.com/gabrtv))
- fix(tests): mock postgresql should wait until initialization complete - [#2037](https://github.com/deis/deis/pull/2037) ([@gabrtv](https://github.com/gabrtv))
- docs(client readme): remove travis build status icon - [#2036](https://github.com/deis/deis/pull/2036) ([@Joshua-Anderson](https://github.com/Joshua-Anderson))
- feat(contrib): add bumpver tool to help with semantic version releases - [#2015](https://github.com/deis/deis/pull/2015) ([@mboersma](https://github.com/mboersma))
- style(publisher): go fmt - [#2032](https://github.com/deis/deis/pull/2032) ([@bacongobbler](https://github.com/bacongobbler))
- feat(controller): restart the app if there is a failure. - [#2019](https://github.com/deis/deis/pull/2019) ([@aledbf](https://github.com/aledbf))
- ref(data-units): use ubuntu:14.04 instead of deprecated deis/base - [#2025](https://github.com/deis/deis/pull/2025) ([@mboersma](https://github.com/mboersma))
- chore(controller): remove unused django-yamlfield from requirements - [#2023](https://github.com/deis/deis/pull/2023) ([@mboersma](https://github.com/mboersma))
- docs(deisctl): document DEISCTL_UNITS better - [#2017](https://github.com/deis/deis/pull/2017) ([@Xe](https://github.com/Xe))
- fix(tests): shrink deis pull image by 200MB - [#2014](https://github.com/deis/deis/pull/2014) ([@gabrtv](https://github.com/gabrtv))
- fix(router): Set default values in /deis/router - [#1938](https://github.com/deis/deis/pull/1938) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- Update gunicorn to support dynamic configuration reload - [#2004](https://github.com/deis/deis/pull/2004) ([@gabrtv](https://github.com/gabrtv))
- feat(router): image without development libraries to reduce the size. - [#1986](https://github.com/deis/deis/pull/1986) ([@aledbf](https://github.com/aledbf))
- fix(controller): work around fleet state reporting on deis run - [#1978](https://github.com/deis/deis/pull/1978) ([@gabrtv](https://github.com/gabrtv))
- fix(logger) small logger fixes - [#2001](https://github.com/deis/deis/pull/2001) ([@bacongobbler](https://github.com/bacongobbler))
- Use Real CoreOS on DigitalOcean - [#1776](https://github.com/deis/deis/pull/1776) ([@nathansamson](https://github.com/nathansamson))
- Chaos test framework with improved error handling - [#1913](https://github.com/deis/deis/pull/1913) ([@gabrtv](https://github.com/gabrtv))
- chore(builder): migrate to cedar-14 stack - [#1975](https://github.com/deis/deis/pull/1975) ([@bacongobbler](https://github.com/bacongobbler))
- feat(tests): Show all etcd keys on error - [#2009](https://github.com/deis/deis/pull/2009) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- fix(controller): Use correct entrypoint for run - [#1985](https://github.com/deis/deis/pull/1985) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- docs(installing_deis): remove xip.io instructions for ELB - [#2003](https://github.com/deis/deis/pull/2003) ([@carmstrong](https://github.com/carmstrong))
- fix(builder): Non-root slugrunner and slugbuilder - [#1972](https://github.com/deis/deis/pull/1972) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- docs(deisctl): clarify deisctl version when using install.sh - [#1991](https://github.com/deis/deis/pull/1991) ([@carmstrong](https://github.com/carmstrong))
- ref(tests): update details in CI node setup script - [#1983](https://github.com/deis/deis/pull/1983) ([@mboersma](https://github.com/mboersma))
- fix(builder): restore VOLUME instruction so builder does not stack overlay filesystems - [#1996](https://github.com/deis/deis/pull/1996) ([@gabrtv](https://github.com/gabrtv))
- fix(*): Announce the published port to etcd - [#1864](https://github.com/deis/deis/pull/1864) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- ref(builder): remove volume definition in Dockerfile - [#1984](https://github.com/deis/deis/pull/1984) ([@carmstrong](https://github.com/carmstrong))
- fix(deisctl): typos in publisher unit file - [#1990](https://github.com/deis/deis/pull/1990) ([@bacongobbler](https://github.com/bacongobbler))
- ref(Dockerfiles): base Dockerfiles on ubuntu:14.04 - [#1878](https://github.com/deis/deis/pull/1878) ([@mboersma](https://github.com/mboersma))
- ref(scheduler): introduce deis/publisher - [#1708](https://github.com/deis/deis/pull/1708) ([@bacongobbler](https://github.com/bacongobbler))
- chore(*): remove deis-builder-data - [#1917](https://github.com/deis/deis/pull/1917) ([@carmstrong](https://github.com/carmstrong))
- docs(vagrant): bump version to v1.6.5 - [#1977](https://github.com/deis/deis/pull/1977) ([@bacongobbler](https://github.com/bacongobbler))
- fix(tests): data containers should not be shared - [#1969](https://github.com/deis/deis/pull/1969) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- chore(*): bump CoreOS to 452.0.0 - [#1940](https://github.com/deis/deis/pull/1940) ([@carmstrong](https://github.com/carmstrong))
- ref(tests): move test-nightly to test-latest - [#1965](https://github.com/deis/deis/pull/1965) ([@gabrtv](https://github.com/gabrtv))
- Cleanup Makefile and test suites in preparation for new CD pipeline - [#1951](https://github.com/deis/deis/pull/1951) ([@gabrtv](https://github.com/gabrtv))
- ref(Vagrantfile): align with upstream coreos-vagrant - [#1881](https://github.com/deis/deis/pull/1881) ([@mboersma](https://github.com/mboersma))
- fix(deisctl): create unit download URL properly after move to subdir - [#1961](https://github.com/deis/deis/pull/1961) ([@mboersma](https://github.com/mboersma))
- fix(docs): clean up sources and treat warnings as errors - [#1952](https://github.com/deis/deis/pull/1952) ([@mboersma](https://github.com/mboersma))
- fix(deisctl): install only deisctl - [#1950](https://github.com/deis/deis/pull/1950) ([@bacongobbler](https://github.com/bacongobbler))
- docs(deisctl): add unit search paths behavior to README - [#1941](https://github.com/deis/deis/pull/1941) ([@mboersma](https://github.com/mboersma))
- fix(CHANGELOG): use SSL for github URLs, recreate change entries - [#1943](https://github.com/deis/deis/pull/1943) ([@mboersma](https://github.com/mboersma))
- fix(readme): use relative link to deisctl in repo - [#1946](https://github.com/deis/deis/pull/1946) ([@gabrtv](https://github.com/gabrtv))
- fix(router): gzip content types syntax fixed - [#1939](https://github.com/deis/deis/pull/1939) ([@johanneswuerbach](https://github.com/johanneswuerbach))
- ref(deisctl): move Deis Control Utility to github.com/deis/deis/deisctl - [#1926](https://github.com/deis/deis/pull/1926) ([@mboersma](https://github.com/mboersma))
- chore(deis): bump version to 0.13.0-dev - [#1908](https://github.com/deis/deis/pull/1908) ([@bacongobbler](https://github.com/bacongobbler))
- feat(userdata): add deisctl to the coreos install - [#1903](https://github.com/deis/deis/pull/1903) ([@Xe](https://github.com/Xe))

For details, please see [CHANGELOG.md](https://github.com/deis/deis/blob/master/CHANGELOG.md).

### Community Shout-Outs

We want to thank the following Deis community members for creating GitHub issues,
providing support to others, and working on various Deis branches:

@achannarasappa: Build hook error: Server Error (500)
@aledbf: Restrict published containers, logspout message too long error, Router restarts, Add git commit to image env, Change to controller scheduler for fleet v0.8.3, Retry Fleet scheduling operations, feat(controller): restart the app if there is a failure., feat(router): image without development libraries to reduce the size.
@chuenlye: Ownership of /usr/local/bin was changed when installing deisctl
@cmshetty: Fleetctl shows old dead and failed units., Web process fails to start - "ruby: command not found", Config set for integer gives internal error.
@cn28h: deisctl platform start requires several runs to succeed
@gust1n: Deis publisher improvements
@ianblenke: Feature request: deis users:list
@intellix: builder: issue with check-repos script removing an active repository
@jaystewart: Vagrant - deisctl start platform - deis-router@1.service: failed
@johanneswuerbach: deis run is printing the output of the previously executed command, deisctl installation shouldn't use sudo, deisctl unit lookup should be the same for scheduling and refresh, deisctl should warn about outdated unit files, Feature: deis restart, controller is not reloaded when template changes, App containers are not waiting for the registry , docker hub images are containing the wrong version, make discovery-url fails silently, Build status badge, feat(router): Changed store hostname to deis-store, fix(router): Use official javascript content type, fix(tests): Increased test timeout for smoke tests, fix(router): Set default values in /deis/router, feat(tests): Show all etcd keys on error, fix(controller): Use correct entrypoint for run, fix(builder): Non-root slugrunner and slugbuilder, fix(*): Announce the published port to etcd, fix(tests): data containers should not be shared, fix(router): gzip content types syntax fixed
@Joshua-Anderson: `deisctl install platform` throws logger-data template not found, docs(standards): remove [skip ci] instructions, docs(client readme): remove travis build status icon
@kingcody: Builder and Controller "hang" on fresh install
@lpickerson86: some admin services wake up after run commnad on app
@nathansamson: Running 2 web processes in one application, Use Real CoreOS on DigitalOcean
@ngpestelos: Failed to install deisctl, Multiple publishers running on the same node, X-Deis-Builder-Auth not checked?
@peterrosell: Missing instruction in "Get Deis" section 02 , solved: local DNS not resolving for local.deisapp.com
@pgrm: Update the documentation on how to deploy on DigitalOcean
@PierreKircher: doc > baremetal, deis-store > database, restart behavior of deisctl, master > builder in endless loop on GCE, (DOC) upstream new builds with privatregistry on boot2docker + ngrok
@scottrobertson: Few issues with Digital Ocean
@sstarcher: Fleet scheduler to not get memory/cpu scheduling
@tobyhede: Deploy of example app fails with 'invalid compressed data--format violated', Error on install: Failed getting response from http://127.0.0.1:4001, ==> deis-1: No etcd discovery URL set in /tmp/vagrantfile-user-data
@tombell: Installation of deisctl results in 404 error
@vincentpaca: deisctl start platform keeps timing out.
@Xe: deisctl causes the cluster to implode, Basic user operations, Metadata tagging for deis unit installs, Installing deis client on OSX causes failure in cleanup process, install fails, pgbouncer in buildpack fails due to missing system library, Feature request: ability to see who you are logged in as, deisctl doesn't follow versioning for default installs, deisctl refresh-units defaultly tries to write to non-user-owned space, Suggestion: setting where administrator needs to confirm new registrations, docs(deisctl): document DEISCTL_UNITS better, feat(userdata): add deisctl to the coreos install

The Deis community continues to grow, and Deis wouldn't be here without you! If we slighted your contribution to this release, please let us know so we can update.

## Known Issues

### etcd failure when losing a host

We have sometimes seen etcd/fleet issues when losing a cluster host. This issue is tracked in the [fleet project](https://github.com/coreos/etcd/issues/863). We are working with the CoreOS team to identify the root cause, and will update to a new CoreOS release once the issue is fixed.

## What's Next?

### Deis Upgrades

As Deis nears a stable release, our first priority is making sure Deis upgrades are fast, painless, and backwards compatible. We are devoting significant resources to this effort, and are working closely with the CoreOS team who has a great deal of experience with rolling upgrades. We recently [showed off](http://gabrtv.github.io/deis-coreos-meetup-2014/#/) the update system at the CoreOS meetup in SF--coming soon!

### Platform Security & HA

With Deis being used in a growing number of real-world deployments, we need to address remaining [security](https://github.com/deis/deis/issues?labels=security&state=open) issues as well as the [high-availability](https://github.com/deis/deis/issues/984) of the platform itself. Deis components and hosted apps are now fronted by a user-defined number of routers, and other HA features are prerequisites for our impending stable release.

### Automated Testing

Distributed systems are notoriously difficult to test, but automated testing is critical for Deis. The Deis project will continue to invest in quality and to push the limits of what is possible with Docker and automated testing. Watch Deis get even better at http://ci.deis.io/.

## Future

### Service Gateway

Deis must make it simple for ops folks to publish a set of reusable backing services (databases, queues, storage, etc) and to allow developers to attach those services to applications. This will be done in a loosely coupled way, following Twelve Factor best practices. You can review the initial implementation and follow progress [on this GitHub issue](https://github.com/opdemand/deis/issues/231).

### Interactive `deis run`
Although `deis run` executes individual admin commands inside containers, Deis doesn't yet support long-running interactions, such as `deis run bash`. Once this infrastructure is in place, Deis can implement log tailing and other real-time features.

## How can you help?

* Star our [GitHub repository](https://github.com/opdemand/deis)
* Help spread the word about [@opendeis](http://twitter.com/opendeis) on Twitter
* Join the conversation in the [#deis channel](https://botbot.me/freenode/deis/) on Freenode
* Pick an [easy-fix issue](https://github.com/deis/deis/issues?labels=easy-fix&state=open) and start contributing!

Learn about other ways to [get involved](http://deis.io/get-involved/) on our website.
