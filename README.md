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

    [Unit]

    Description=/etc/rc.local Compatibility
    ConditionPathExists-/etc/rc.local

    [Service]

    Type=forking
    ExecStart=/etc/rc.local start
    TimeoutSec=0
    StandardOutput=tty
    RemainAfterExit=yes
    SysVStartPriority=99

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
