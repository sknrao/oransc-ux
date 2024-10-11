. This work is licensed under a Creative Commons Attribution 4.0 International License.
.. SPDX-License-Identifier: CC-BY-4.0

IOS-MCN User-Experience
=======================

This document describes the experience of IOSMCN project in using O-RAN-SC solutions.

About IOSMCN
------------
The Indian Open-Source Software Platform for end-to-end Mobile Communication Networks (IOS-MCN) will accelerate the development and deployment of Mobile Communication (5G/6G) products and services by the vendors.

It is a collaboration between academia, government, and the Indian Telecom Ecosystem (vendors, service providers, companies, and startups) to leverage the global open-source ecosystem and establish a common forum for open source technology projects and solutions from India, by India.

The IOS-MCN Consortium provides a neutral, democratic, and trusted platform for the translation of 5G/6G innovation and research into commercially deployable Open Source software.

About the Work
--------------
The work is about adding SMO solution for IOS-MCN based on open-sources. The below figure shows the scope of the work. SMO of IOSMCN provides the following:

- Automated deployment of Kubernetes Cluster and Docker Environment
- Automated Deployment of RAN, Core and OAM Components.
- Configuration of RAN and Core through GUI.
- Visualization of Performance metrics, Faults and Logs.

The first release of IOS-MCN mostly cover the OAM component of the SMO.

.. image:: images/smo.png
   :scale: 10%


The OAM Architecture
--------------------

The overall OAM architecture of IOS-MCN is shown below.

.. image:: images/oam.jpg
   :scale: 25%

Experience
----------
We will describe the experience - in terms of lessons learnt, challenges faced, choosing right solution among the available alternatives, etc, - for each of the individual components one by one.

SDN-Controller based configuration of RAN
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The project initially explored the light-weight configuration solution for RAN. Developing a custom Netconf client application is not a challenge, However, features such as additional features such as message-handling, topology management, and inventory, which are already part of an SDN controller, makes a strong case for SDN-Controller based solution. In addition, all available open-source RAN configuration solutions are SDN-based (we couldn't find what solution srsRAN is using). 

Alternatives:
#############
1. ONAP's SDNC and SDNC-Web - part of O-RAN-SC's OAM.
2. ONOS-Config 
3. OpenMPlane (For RU configuration).

ONOS-Config is based on gNMI, and lacked Netconf Support. Converting from gNMI to Netconf adds additional work. Hence we decided to use SDNC/R (ODL) from o-ran-sc/oam.

We will be exploring OpenMplane for the next release of IOS-MCN.

Challenges:
###########
Currently, the SDNC-Web's configuration application has lot of issues in processing the configuration (get configuration) and also while making the actual changes to the configurable parameters.

Tips:
#####


VES-Collector
~~~~~~~~~~~~~

Alternatives:
#############
1. VES-Collector from ONAP - which is used by the O-RAN-SC's OAM project.
2. VES-Collector from the O-RAN-SC's SMO project.

The VES-Collector from smo-ves is not actively maintained. Hence, we decided to use the VES-Collector from ONAP, which is part of O-RAN-SC's OAM project. 

User Contact for IOS-MCN
************************
Name: Sridhar K. N. Rao
email: sridharkn@u.nus.edu



