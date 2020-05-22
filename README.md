# Ph.D. Thesis - Generation of High-Speed Network Device from High-Level Description

A dissertation thesis submitted to the Faculty of Information Technology, Czech Technical University in Prague, in partial fulfilment of the requirements for the degree of Doctor. 

The repository contains the LaTeX sources of my Ph.D. thesis and the defense presentation.

The following list contains required tools:
* LaTeX
* Inkscape
* make
* Dia

The translated PDF can be downloaded [here](text/phd-benacek.pdf).

The project also contains the profile for textstudio (http://www.texstudio.org/) for easier preparation of LaTeX documents.

## Abstract
OpenFlow, as the most popular embodiment of Software-Defined Networking, provides a
way to network dataplane configuration at runtime. The OpenFlow specification strictly
defines a set of supported protocols and actions for further processing of incoming traffic
(i.e., switches are still mostly fixed). However, modern requirements on networking hardware
have a dynamic character and administrators of high-end networks want to react to
new protocols, security threats, novel approaches in traffic engineering, and so on. This
isn’t feasible with static network hardware and leads to the need to replace the hardware
more often than desired.
The aim of my dissertation thesis is to provide the process of mapping from abstract
language to the architecture of network device which is suitable for automatic generation
and capable to hit processing speed of 100 Gbps in single FPGA. The architecture of
network device is based on predefined interfaces and modules which are connected to a highspeed
processing pipeline. The text provides details of transformation process to individual
blocks of network device: parser, deparser, Match+Action table, Match+Action router and
Match+Action group. The text also demonstrates the usage of High-Level Synthesis tools
to provide a custom processing engine which is capable to hit speed of 100 Gbps. Finally,
the text provides three use cases for demonstration of flexibility and easy extensibility
with new protocols and actions. Each use case was described in P4 language, translated to
VHDL and tested in real hardware environment. The results show that generated devices
are capable to meet throughput in range from 77.6 to 100 Gbps.

**Keywords**: FPGA, High-Level Synthesis, Transformation, P4, SDN, High-Speed Computer Networks, 100 Gbps, VHSIC Hardware Description Language
