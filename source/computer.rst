Computer Overview and Configuration
===================================

Minireach has two internal computers which run a
Long Term Support (LTS) release of Ubuntu (14.04) and an LTS release of
ROS (Indigo). These releases are intended to give long-term stability to
the system.

.. embed-user-accounts-start

Default User Account
--------------------

Each robot ships with a default user account, with username `ubuntu` and
password `ubuntu`. It is recommended to change the password when
setting up the robot.

Networking
----------

The robot currently has its own router with both Ethernet and Wi-Fi.
The Jetson TX1 and raspberry pi have static IP adresses assigned based on
their respective MAC addresses by the DHCP server on the router.

The static IPs are:
    TODO

.. warning::

    Never drive the robot with an Ethernet cable attached.

Connecting the Robots Wireless Network
------------------------------------------

The ssid for the network is `minireach_network` (alternatively `minireach_network_5G`)
and the password is `minireach`.

Clock Synchronization
---------------------

It is recommended to install the chrony NTP client on both robots and desktops
in order to keep their time synchronized. To install chrony on Ubuntu:

::

    > sudo apt-get update
    > sudo apt-get install chrony
    > Not complete (setup local time server)

.. _upstart_services:

Upstart Services
----------------

Minireach uses robot_upstart to start and manage various services on the robot.

Upstart service can be restart with the `service` command. For instance, to
restart the robot drivers:

::

    >sudo service minireach stop
    >sudo service minireach start

To setup drivers for autostart:

::
    >rosrun robot_upstart install minireach_bringup/launch/concert_client.launch

To remove autostart:

::
    >rosrun robot_upstart uninstall minireach

Log Files
---------

A number of log files are created on the robot. The most recent logs related to robot_upstart
services can be viewed using: sudo tail /var/log/upstart/minireach.log -n 30
