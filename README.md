# Enable-Autorun-in-Linux-on-rc.local
 Autorun program in linux 

=====================================================

## (1)

     sudo systemctl status rc-local

## (2)

     sudo systemctl enable rc-local

## (3)
     sudo nano /etc/systemd/system/rc-local.service

## paste it in rc-local.service ##

-------------------------------------------------------

    # /etc/systemd/system/rc-local.service
    #  SPDX-License-Identifier: LGPL-2.1+
    #
    #  This file is part of systemd.
    #
    #  systemd is free software; you can redistribute it and/or modify it
    #  under the terms of the GNU Lesser General Public License as published by
    #  the Free Software Foundation; either version 2.1 of the License, or
    #  (at your option) any later version.

    # This unit gets pulled automatically into multi-user.target by
    # systemd-rc-local-generator if /etc/rc.local is executable.

     [Unit]
     Description=/etc/rc.local Compatibility
     Documentation=man:systemd-rc-local-generator(8)
     ConditionFileIsExecutable=/etc/rc.local
     After=network.target

     [Service]

     Type=forking
     ExecStart=/etc/rc.local start
     TimeoutSec=0
     StandardOutput=tty
     RemainAfterExit=yes
     SysVStartPriority=99
     GuessMainPID=no

     # /usr/lib/systemd/system/rc-local.service.d/debian.conf



     [Unit]
     # not specified by LSB, but has been behaving that way in Debian under SysV
     # init and upstart
     After=network-online.target

     # Often contains status messages which users expect to see on the console
     # during boot
     [Service]
     StandardOutput=journal+console
     StandardError=journal+console



     [Install]

     WantedBy=multi-user.target


-----------------------------------------------------

## (4)

     sudo nano /etc/rc.local

## paste it in rc-local ##


----------------------------------------------------

     #!/bin/bash

     note- enter your path which you want to run after boot

     ex- python3 /DEsktop/atul/iot/developer/run.py

     exit 0

--------------------------------------------------

## (5)

     sudo chmod +x /etc/rc.local

## (6)

     sudo systemctl enable rc-local



After successful creation 
[Output]

==================================================================================================================

Created symlink /etc/systemd/system/multi-user.target.wants/rc-local.service → /etc/systemd/system/rc-local.service.

==================================================================================================================


## (7)


    sudo systemctl start rc-local

## (8)

     sudo systemctl status rc-local

## (9)

      sudo shutdown -r now





Autorun has started successfully 

-----------------------------------------------------------------------------------

                                                                                                #### ATUL KUMAR
                                                                                                #### IOT DEVELOPER
