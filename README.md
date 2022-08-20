# Turtlebot 3's VSCode guide

## Problem
To start up the VSCode server on the raspberry pi server on turtlebot3, you need internet access.  
But the problem is that the server doesn’t have an internet connection either.

Raspberry pi itself acts as a Wi-Fi hotspot, which allows you to connect via Wi-Fi.  
As a result, when you connected to the robot with Wi-Fi, you also cannot access the internet.  
<span style="color:red">**EXCEPT**</span> you have another way to access the internet (In this case, LAN Cable)

So, the point is that we have to install the VSCode server on the turtlebot3 using the local side's internet.

## Requirement
1. Internet connection. (Both Wi-Fi and LAN Cable)
2. A computer that can connect to both Wi-Fi and LAN at the same time.
3. VSCode with “Remote Development” Extension
4. Allow access to your computer via SSH
	- For Windows
		- First, Open up Powershell as the administrator  
			(<span style="color:red">**Must be in administrator mode!!**</span> otherwise, you might not be able to run the following command)
		- Second, run the command `Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0`
	- For macOS: please follow this guide https://support.apple.com/en-gb/guide/mac-help/mchlp1066/mac

## Procedure
1. Start a robot and wait for the Wi-Fi name of the robot (`TB3_AP_<robot_name>`) to show up.
2. On your computer
	- connect to a LAN cable (make sure that it has the internet connection)
	- connect to the robot’s Wi-Fi, also check up the IP of the robot (We have to use it later)
	- make sure that you still can connect to the internet after connecting to the robot's Wi-Fi  
	(or try to open [https://code.visualstudio.com/](https://code.visualstudio.com/))
3. In VSCode
	1. Open the command palette
	- For Windows: type `Ctrl+Shift+P`
	- For macOS: type `Cmd+Shift+P`
	2. Type `open user setting`, select then enter
	![](images/open_user_setting.png?raw=true)  
	(<span style="color:red">**NOT THE ITEM THAT ENDS WITH JSON!!**</span>)
	3. Type `remote ssh local` in the `Search settings` field 
	4. In **Remote.SSH: Local Server Download** setting, Select the choice to `always`
	![](images/local_server_download.png?raw=true)  
	5. Connect to the robot using command palette -> remote SSH -> connect to host...

## Note
When you use VSCode in the normal environment after performing this guide (Connect to your normal Wi-Fi), VSCode might upgrade itself, and it will break the VSCode server on the robot.  
If there is an error that might occur after a while, **you need to connect your computer to the LAN and connect to the Robot's Wi-Fi at the same time** for upgrading the VSCode server when you want to do your assignment on the robot.

If there is any unexpected error that couldn't be solved with this guide, message me directly.
