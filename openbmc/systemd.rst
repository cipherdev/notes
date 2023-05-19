Systemd How To
==============
OpenBMC uses systemd to manage all processes. It has its own set of target and service units to control which processes are started.

*  `Unit`: Units are the basic framework of all systemd work.

* `Service`: Services are a type of unit, that define the processes to be run and execute.

*  `Target`: Targets are another type of unit, they have two purposes:

Define synchronization points among services. Define the services that get run for a given target.
On an OpenBMC system, you can go to `/lib/systemd/system/` and see all of the systemd units on the system. You can easily cat these files to start looking at the relationships among them. Service files can also be found in /etc/systemd/system and /run/systemd/system as well.

* `systemctl` is the main tool you use to interact with systemd and its units.

Commands
~~~~~~~~
* Viewing the Status of a Service::

    systemctl status {unit-name}

* List all services unit as follows::

    sudo systemctl --type=service

* List all see mount type units::

    sudo systemctl --type=mount

* Display all systemd timer units::

    systemctl -t timer

* To show all installed unit files use::

    systemctl list-unit-files

* List units that systemd currently has in memory::

    systemctl list-units
    systemctl list-units | more
    systemctl list-units | grep keyword
    # filter by unit types
    systemctl list-units --type service
    systemctl list-units --type timer
    # List units/services failed
    systemctl list-units --failed
    systemctl list-units --state failed
    ## filtering by unit type ##
    systemctl list-units --state failed --type service
    systemctl list-units --state failed --type timer

* Verify that if a service enabled or not, run::

    systemctl is-enabled nginx.service

* To see full outputs for debug service issue pass the `--full` or `-l` option::

    systemctl status phosphor-reboot-host@0.service -l
    systemctl status phosphor-reboot-host@0.service --full

* Debug and see all log messages related to service using the journalctl command::

    journalctl UNIT=phosphor-reboot-host@0.service

* View systemd service/unit file source::

    systemctl cat phosphor-reboot-host@0.service

----------------

A command like refer Cyberciti_.

.. _Cyberciti: https://www.cyberciti.biz/faq/systemd-systemctl-view-status-of-a-service-on-linux

---------------