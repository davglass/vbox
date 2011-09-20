Dav's VirtualBox server setup
-----------------------------

This is a simple set of scripts that I tossed together to help me manage my VirtualBox server.

Server Setup
------------

My local server is a simple Ubuntu server (currently running 11.04) and I have VirtualBox installed and configured already.

File Structure
--------------

My scripts rely on all VM's to live under `/machines`

	sudo mkdir /machines
	sudo chown -R $USER /machines

Scripts
-------

   * VBoxCreate
	Helps you create a VM from a local ISO
   * VBoxControl
	Aids in starting and stopping multiple VM's
   * VBoxEject
	Helper script to eject a previously mounted CD
   * VBoxMountCD
	Mount an ISO as a CD


My /machines/images Directory
-----------------------------

	ubuntu-10.04.1-desktop-i386.iso
	ubuntu-10.04.1-server-i386.iso
	ubuntu-10.10-desktop-i386.iso
	ubuntu-11.04-server-i386.iso
	VBoxGuestAdditions_4.0.8.iso
	Win7Pro_32bit.iso
	winxp.iso

**I do have paid licenses for all my required images**

Examples
--------

	VBoxCreate myubuntuhost Ubuntu ubuntu-10.04.1-server-i386.iso
	//After
	VBoxManage modifyvm myubuntuhost --vrdeport 4001

	VBoxCreate WinXP-IE6 WindowsXP winxp.iso
	//After
	VBoxManage modifyvm WinXP-IE6 --vrdeport 4002
	
	VBoxCreate Win7 Windows7 Win7Pro_32bit.iso
	//After
	VBoxManage modifyvm Win7 --vrdeport 4003


	VBoxControl start myubuntuhost
	VBoxControl start Win7
	VBoxControl start all

	VBoxControl stop myubuntuhost
	VBoxControl stop Win7
	VBoxControl stop all

	VBoxMountCD WinXP-IE6 VBoxGuestAdditions_4.0.8.iso
	VBoxEject WinXP-IE6
