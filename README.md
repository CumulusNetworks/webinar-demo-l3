# cldemo-netq-l3

This demo will install Cumulus Linux [NetQ](https://docs.cumulusnetworks.com/display/DOCS/Using+netq+to+Troubleshoot+the+Network) on the Cumulus [reference topology](https://github.com/cumulusnetworks/cldemo-vagrant). Please vist the reference topology github page for detailed instructions on using Cumulus Vx with Vagrant.

![Cumulus Reference Topology](https://github.com/CumulusNetworks/cldemo-vagrant/raw/master/cldemo_topology.png)

Quickstart
------------------------
* git clone https://github.com/cumulusnetworks/cldemo-vagrant
* cd cldemo-vagrant
* vagrant up
* vagrant ssh oob-mgmt-server
* sudo su - cumulus
* git clone https://github.com/CumulusNetworks/webinar-demo-l3.git
* cd webinar-demo-l3
* ansible-playbook -s configure.yml
* ssh leaf01

Details
------------------------

This demo will configure a layer 3 BGP network. The demo is downloaded onto the `oob-mgmt-server` under the `cumulus` user. It assumes the network is up and running (via `vagrant up`) but it **has not** yet been configured. The playbook `configure.yml` will configure BGP (or OSPF) on all spine and leafs as well as configure the hosts. 

You can change the protocol in the properties.yml file to "ospf" to configure the CLOS with unnumbered OSPF rather than BGP. Run the reset playbook before switching protocols to ensure a clean slate to start the configuration on.


Resetting The Topology
------------------------
If a previous configuration was applied to the reference topology, it can be reset with the `reset.yml` playbook provided. This can be run before configuring netq to ensure a clean starting state.

    ansible-playbook -s reset.yml
