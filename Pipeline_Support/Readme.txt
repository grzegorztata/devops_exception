Project variable: RDP_Disconnect: For pipeline support.  If true allows RDP_Disconnect to run.  If false running RDP_Disconnect will have no effect
Project variable: RDP_Disconnect_Script_Filename: The script used to disconnect the RDP sessions and connect the session to the local console graphics device
	"C:\\Regression\\In Development\\Keplar_Regression\\Pipeline_Support\\Disconnect.bat"
Keyword test: RDP_Disconnect - This is basically a wrapper for the script Pipeline_Support.  It must run first before any apps are open.
Script: Pipeline_Support - Runs Disconnect.bat as administrator. 
Disconnect.bat - Is run as administrator at the the start of all tests before any apps are opened.
	This searches for any RDP sessions under the currently logged in user and re-connects them to the console device.
	---------------------------------------------
	for /f "skip=1 tokens=3" %%s in ('query user %USERNAME%') do (
	  %windir%\System32\tscon.exe %%s /dest:console
	)
	---------------------------------------------


	