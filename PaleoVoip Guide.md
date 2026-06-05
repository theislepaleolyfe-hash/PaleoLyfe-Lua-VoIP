### GameBros Proton Windows Test Upload



1\. Game Directory 

&#x09;/home/container/TheIsle/Content/



2\. Find or Install 

&#x09;UE4SS/



3\. Create

&#x09;Mods/



4\. Upload Zip, should read as 

&#x09;/home/container/TheIsle/Content/UE4SS/Mods/

New > /home/container/TheIsle/Content/UE4SS/Mods/PaleoVoIP/



5\. Create Bridge File

&#x09;/home/container/

New > /home/container/paleo\_bridge/



6\. Upload Python Bridge Contents from ZIP into bridge FILE

&#x09;bridge.py

&#x09;start\_bridge.sh

&#x09;README.txt

&#x09;Auto\_heal.sh



7\. Open console, run both:

&#x09;chmod +x /home/container/paleo\_bridge/start\_bridge.sh

&#x09;chmod +x /home/container/paleo\_bridge/auto\_heal.sh





8\. AutoStart Bridge

&#x09;/home/container/start.sh

&#x09;	scroll to bottom of file add:

&#x09;bash /home/container/paleo\_bridge/auto\_heal.sh \&

&#x09;bash /home/container/paleo\_bridge/start\_bridge.sh \&

&#x09;	ensure the auto\_heal.sh code is first and the start\_bridge.sh is last



9\. Restart Server

&#x09;	Console output should read as: 

&#x09;\[PaleoVoIP] Auto-restart bridge is now running.

&#x09;\[PaleoVoIP] Starting bridge...



### Live Testing



1. Open Mumble

&#x09;connect to server; ensure positional audio is enabled

2\. Join Evrima server

3\. Test with other users



4\. Check bridge logs 

&#x09;	Should see lines like: 

&#x09;fresh: steam\_id64=unknown pos=(1234.56, 789.01, 345.67)

&#x09;	"fresh" means it's working



### Troubleshooting

1. UE4SS Failed to load

&#x09;	Check: 

&#x09;/home/container/TheIsle/Content/UE4SS/UE4SS.log

&#x09;	Look for lines like "**Loaded mod: PaleoVoIP**"

&#x09;	Ensure no errors like "**Failed to load mod.txt**"

&#x09;	Confirm path reads as:

&#x09;/TheIsle/Content/UE4SS/Mods/PaleoVoIP/



2\. Check Script Output

&#x09;	Navigate to root file:

&#x09;/TheIsle/Content/UE4SS/Mods/PaleoVoIP/

&#x09;	Confirm "**paleovoip\_positon.json**" exists

&#x09;	Open it, ensure values update while moving in game

&#x09;	If the file is missing, the script isn't running



3\. Validate JSON Content

&#x09;	Open:

&#x09;paleovoip\_position.json

&#x09;	Ensure file is JSON valid with no trailing commas

&#x09;	Confirm fields: **position\_m**, **front**, **top**, **context**



4\. Check Python Bridge Startup 

&#x09;	Check console on booting, should read:

&#x09;\[PaleoVoIP] Auto-restart bridge is now running.

&#x09;	Start.sh should include:	

&#x09;bash /home/container/paleo\_bridge/start\_bridge.sh \&

&#x09;	Run (below) command if permission denied:

&#x09;chmod +x start\_bridge.sh



5\. Check Bridge Logs for fresh data

&#x09;	If fresh is unchanged, JSON is not updating properly

&#x09;	If there are decode errors, JSON is malformed



6\. Check MumbleLink Shared Memory

&#x09;	Ensure the bridge is running under the same User as the server

&#x09;	Restart mumble after server restart



