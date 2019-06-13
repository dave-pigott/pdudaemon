# Switchable device control API

The proposal is for controlling any switchable device (PDU, USB hub, Relay, … etc?)

The interface will support the following functionality:

Mode 1 - First state to put the port into
	Off
	On

Mode 2 - Second (optional) state to put the port into
	Off
	On

Get - Get information
	Status
	-1 = Unknown
		0 = Off
		1 = On
	List
		List of devices this instance can control
		Returns a list of device hostnames and their types (PDU, USB, Relay)

Delay - Delay in seconds between setting mode 1 and mode 2
	Default 0

Hostname - The name of the device you wish to control
hostname, identifier, IP address etc

Port  - The device port you wish to control
Integer or other port identifier(?)

Retries - Number of times to retry setting the port (default=3)
The proposal is that there will be a random delay, between the retries, of up to “Retry Delay Max” seconds. Maybe we  can add a parameter to fine tune that maximum?

Retry Delay Max
	Integer in seconds. Default 5

Sleep After - Delay in seconds after command is executed (default 0)

Sleep Before - Delay in seconds before command is executed (default 0)

Sync - Boolean to determine whether to wait for completion - default = true
If True, wait for completion and return success (0) or failure code (1 if error code not determinable, otherwise error code).
If false, this will merely return 0 for a successful queueing of the command, 1 for a failure to queue the command

Timeout - Time in seconds to wait for command to fail (default 10 seconds)

