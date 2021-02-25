YANG Suite core Django application.

Capable of dynamic discovery of installed application plugins. Provides common library APIs for logging, filesystem access, GUI appearance and behavior, and client-server communication.

Authors: Members of the Cisco YANG Suite development team.
Supports: Python 3.6, Python 3.7, Python 3.8
YANG Suite can be installed as a Docker container or through Python package management. Docker-compose is the recommended install.

Requires about 3.5GB of memory to load large Cisco native models.

Refer to this page for the YANG Suite installation guidance https://github.com/CiscoDevNet/yangsuite

Background

IOS XE Release: 17.3



Module Topics:

Introduction to NETCONF/YANG

Enable NETCONF/YANG

YANGSuite

Conclusion



Introduction to NETCONF/YANG

In this section we will look at YANG data models, why we need them, and how to find them. We will use a tool called YangSuite to find the data models we need, and we will write Python scripts using the models.

Login Information

Enable NETCONF/YANG

Before we start using YANG Suite to look at the data models on our switches, we need to run through a few steps to enable NETCONF, which is not on by default.

Open a telnet session to your C9300 switch and Verify AAA and NETCONF are already configured on the device.

C9300#sh run | sec aaa

aaa new-model 

aaa authentication login default local 

aaa authorization exec default local 

aaa session-id common 

C9300#sh run | sec vty  

line vty 0 4  

exec-timeout 0 0 

 length 0  

transport input all 

line vty 5 15  

exec-timeout 0 0  

length 0  

transport input all

C9300#sh run | i netconf 

netconf-yang

C9300#show run | i username 

username admin privilege 15 secret 9 ....