# ConductR release notes

## 1.0.12

* Improved the reliability of connectivity with the experimental Elasticsearch logging feature.
* Released a Docker based image of the full ConductR which may be used by the sandbox for development purposes only. The image name is "typesafe-docker-registry-for-subscribers-only.bintray.io/conductr/conductr" and is now the default for sbt-conductr-sandbox.
* Improved the Visualizer sample with a means to filter bundles.
* Corrected the index name used by ConductR for the experimental Elasticsearch functionality.
* Now permits the disablement of reading the conf/seed-nodes file on startup
  for non-production style environments. For more information please refer to the `--seed-node-file-disabled` option of your distribution's `conf/application.ini`.
* Seed nodes are now provided in an order of their distance from the current node. This provides ConductR with the best chance of seeding with networks that may exist on other availability zones or data centers.
* Fixed a bug where requests to load or scale a bundle could accumulate despite expiring and result in a situation where no further loads or scales would be accepted.

## 1.0.11

* The check command was not indicating a failure exit status when failures occurred
* Included the conductr-kibana bundle as part of ConductR project
* The Elasticsearch host required setting when used with the sandbox
* A file named runtime-config.sh is now favored when a configuration bundle is supplied thereby permitting other files to be a part of the configuration bundle

## 1.0.10

* Enabled RPM prefixes to be used with the RPM distribution of ConductR
* Slightly enhanced ConductR's Resource Provider so that it responds to more system stimuli
* Improved bundle load error checking

## 1.0.9

* Fixed the current working directory for the RPM packaging of ConductR
* Enhancements to the experimental Elasticsearch support for consolidated logging
* Improved bundle replication and scaling and tested them to be both reliable within larger clusters on EC2
* Bundles are now restarted when they fail. In the case of a bundle starting and not registering that it has started, ConductR will attempt 3 retries. If a bundle signals that it starts successfully and then fails with a non-zero exit code, ConductR will schedule it for a restart. If a bundle signals that it starts successfully and then exits with a zero exit code (success), ConductR will leave it alone.

## 1.0.8

* Bundle replication and scaling have again been improved given further testing. A 9 node cluster on EC2 with 6 bundles, replicated 9 times and each receiving a scale factor of 4 has shown to be resilient to 3 nodes (1 AZ) disappearing. All bundles are re-balanced on the other nodes. One important and helpful change here is the introduction of a configurable parameter for dampening the ConductR's reaction to cluster membership changes. By default each ConductR service will wait for 2 seconds post receiving any membership change event before acting upon it. This dampening can reduce jitter. Other areas have also been addressed where some of the assumptions about nodes being in a certain state have been removed.

## 1.0.7

* Improved bundle scaling reliability
* Corrected an issue where the name_OTHER_IPS was only being populated with one other IP (same goes for ports)
* The default max size of bundles accepted by ConductR is now 200MB
* Dropped the use of CEE cookies for syslog - structured data is used exclusively
* Arguments can now be provided for bundle components that use Docker

## 1.0.6

* Escaped bash chars in start command
* Split brains are now handled using Akka's new split brain resolver functionality

## 1.0.5

* Verified that ConductR is free from GPL code
* Use SystemV on RHEL6
* Added ability to redirect URLs capturing all information in the URI for service lookup
* Improved scaling reliability drammatically
* Improved the way entries are written to the seed-nodes file for greater success when restarting
* Improved the method by which bundles are terminated - they are now sent SIGTERM and then only SIGKILL if the former times out

## 1.0.4

* Improved the resiliency around starting up bundles
* Bundle scale query implemented for the control protocol
* Internal dependency update
* Improved logging resiliency

## 1.0.3

* Improved the resliency around service lookup within ConductR
* Corrected a problem where a bundle's dynamic ports were not being deallocated.
* Improved some log output at the debug level
* General akka updates

## 1.0.2

* Improved memory management for the ConductR service
* Corrected a problem with validating the loading of bundles
* Improved the debian package to depend on pip3

## 1.0.1

* Improved reliability around scaling bundles

## 1.0.0

Initial release.