## VMware tools for Linux

For Actifio snapshots of VMware VMs, Actifio will use VMware tools to coordinate the snapshot if Application Consitency is requested.  You will need to install VMware Tools into the VM, which will allow pre and post scripts to be run.   

If a VMware snapshot is created with Application Consistency then VMware tools will look for two scripts in the VM.   If for instance the consistency method chosen involves stopping and starting the mysql service, then run the following two commands on the Linux VM to create the VMware pre and post script files:

`echo “service mysql stop” > /usr/sbin/pre-freeze-script`

`echo “service mysql start” > /usr/sbin/post-thaw-script`


Ensure these scripts are executable by issuing chmod 755 against each file:

`chmod 755 /usr/sbin/pre-freeze-script`

`chmod 755 /usr/sbin/post-thaw-script`

Now run a VMware VM snapshot and validate the scripts were run.
