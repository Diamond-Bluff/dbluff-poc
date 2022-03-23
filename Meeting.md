﻿# Platform/PoC/Reference Architecture Meeting Minutes


## 10/5/2021:
Talk about goals:
Define a PoC

PoC ideas:
* Nginx already runs on BF2 (but slowly)
* Nginx on Phantom Lake?
* Mt Evans, Oak Springs Canyon complex, likely not MVP

Actions:
* Set up meeting with Marvell: Octeon <- Kris
* Talk to Intel Phantom Lake people about Diamond Bluff <- Tim

Definition of MVP:
* OS - free
* Free app in container: eg Squid Proxy
* Ability to swap out container
* Freely downloadable
* Blog or other publishing


## 11/1/2021:
Agenda:
* Refresh on previous discussion
* Follow up on card availability: Tim and Kris
   * F5 has Intel Phantom Lake cards incoming
      * Nginx dpdk support provided by vendor (Silicom?)
   * Intel Big Springs Canyon suggested, available now, Xeon, with IPDK
      * FPGA works out of the box
      * Runtime programming all open source, P4 compiler backend closed
      * ACTION: Tom to investigate hardware
      * ACTION: Tim to verify nginx dpdk support can be made available
   * Intel Mt Evans early access possible as well
      * Requires 5.10 and 5.14 for the two cores
* Get input from new members
* Discuss direction and next steps
   * ACTION: Steve to create github repo for PoC working group
   * OS Selection discussion
      * RHEL with dev sub for initial PoC
      * Figure out OS strategy later
* Meeting cadence and date/time
   * Weekly Wed 1-3pm slot


## 11/12/2021:
* Dan: Building cluster
   * Big Springs Canyon on Broadwell with 2x25GbE
   * Mt Evans on Sapphire Rapids with 2x100GbE
   * What OS to deploy?  Start with RHEL 8.5, but Red Hat to investigate OCP options.


## 12/1/2021:
* Introductions to Kyle Mestery and Maxime Coquelin
* Brief review of the goals of the working group and prior discussions


## 12/15/2021:
Merging with the dev platform group
* OS requirements on device
   * Looked at Ubuntu, Fedora, CentOS Stream, and RHEL
   * CentOS Stream 9 with help from the community sounding possible
   * https://wiki.centos.org/SpecialInterestGroup
* Canceling 12/22/2021 meeting


## 1/5/2022:
Light discussion today
* Brief discussion about the Dell presentation, touching on SONiC and whether that applies to DB or not (not general purpose OS)
* Kyle mentioned attempting to get IPDK environment working, will present the process next week.


## 1/12/2022:
* CentOS SIG discussion
* Meeting recorded: https://drive.google.com/file/d/1gPSXwK7xHvFcfWUL3vay7zEaMkjBJQPU/view?usp=sharing


## 1/19/2022:
* CentOS SIG discussion continuation


## 1/26/2022:
Dan Daly and Tim Worsley attended
* Dan update on lab: all parts are in
   * Putting CentOS 8.2 on Mt Evans
   * Putting CentOS 7.x? on Big Springs Canyon
* Tim update on PoC workload
   * Simple learning switch based on nginx
   * Pure software, no acceleration
* How do we generate test load in the Intel lab?


For next session:
* Expecting to not have made progress with hardware, so focus on the test
* Create document describing scenarios, test network, traffic generation, traffic targets
* Goal is to be able to limit test the solution, which F5 hasn’t done yet
* Also look into open source tools or languages for describing the test, so diamond bluff doesn’t have to invent something.  Example would be the open ddos (proposed) standard


## 2/1/2022:
Attendees: Tim Worsley, Tom Rix, Mark Sanders, Steven Royer
* Discussion on virtual development environment:
   * Similar to the ipdk virtual environment
   * Need volunteers to define and implement virtual development environment
      * Tom Rix volunteered!
   * Prefer to start with arm64
   * Start with RHEL for developer (free)
* OS Image requirements
   * DPDK
   * docker/podman
* App requirements
   * Looking to start with open source nginx in a container
   * Use pure CPU cores initially
   * Tim Worsley has agreed to provide this once a platform exists
* Deliveries:
   * General agreement that DPUs aren’t build systems
   * Go into github: recipes, etc
   * Artifactory???  For container images: Prefer quay.io.


## 2/9/2022:
Attendees: Tim Worsley, Steven Royer
* PoC idea
   * Open source nginx with modules like modsec in a container
   * Generate data streams where at least one is “malicious”
      * Container for generating traffic
      * Container as traffic target


## 2/16/2022:
Attendees: Kyle Mestery, Maxime Coquelin, Mark Sanders, Michal Kalderon, Laura JH, Steven Royer
* Review
* Michal Kalderon to look at providing access to Marvell hardware
* Artifacts: look at integrating with github actions + github docker registry


## 2/23/2022:
Attendees: Kyle Mestery, Maxime Coquelin, Mark Sanders, Tom Rix, Dan Daly, Steven Royer, Michal Kalderon
* Dev environment:
   * Provide VM image with some OS (CentOS Stream 9, consider future Debian 11)
      * Tom to talk to Steve about this
* Steve to find out if Red Hat could host some vendor hardware for Diamond Bluff
* Michal to see if something like https://www.redhat.com/en/blog/optimizing-server-utilization-datacenters-offloading-network-functions-nvidia-bluefield-2-dpus can be done on Marvell hardware


## 3/2/2022:
Attendees: Tim Worsely, Michal Kalderon, Laura JH, Steven Royer
* Dev environment follow up: concerns around will adapter vendors support CentOS Stream 9 and Debian 11 (drivers etc…)
   * Marvell: yes, drivers are upstream
   * Intel: ??? no attendees
* Hosting vendor hardware by Red Hat:
   * Answer is no, the plan should be to work this through the foundation when that is set up.
* Action:
   * Tim: put up PR for current PoC plan


## 3/9/2022:
Attendees: Steven Royer, Ted Streete, Michal Kalderon, Mark Sanders, Dan Daly
* Ted leaving the subgroup to focus on other areas
* Tim Worsely out sick
* Kyle on vacation
* Actions:
   * Steve: start OS discussion in slack
   * Steve: update working group description
   * Steve: migrate minutes to github
   * Dan: create document about hardware hosting requirements/options
* Dan: hardware update
   * Big Springs Canyon and Mt Evans in place
   * Access control in place
   * Targeting two weeks for schedule
