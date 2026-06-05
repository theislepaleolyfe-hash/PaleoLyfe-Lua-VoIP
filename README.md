PaleoVoIP – Positional Audio for The Isle: Evrima
-------------------------------------------------

INSTALLATION (GameBrosHosting Windows Proton)

1. Game Directory
	/home/container/TheIsle/Content/

2. Find or Install
	UE4SS/

3. Create
	Mods/

4. Upload Zip, should read as
	/home/container/TheIsle/Content/UE4SS/Mods/
New > /home/container/TheIsle/Content/UE4SS/Mods/PaleoVoIP/

5. Create Bridge File
	/home/container/
New > /home/container/paleo_bridge/

6. Upload Python Bridge Contents from ZIP into bridge FILE
	bridge.py
	start_bridge.sh
	README.txt
	Auto_heal.sh

7. Open console, run both:
	chmod +x /home/container/paleo_bridge/start_bridge.sh
	chmod +x /home/container/paleo_bridge/auto_heal.sh


8. AutoStart Bridge
	/home/container/start.sh
		scroll to bottom of file add:
	bash /home/container/paleo_bridge/auto_heal.sh &
	bash /home/container/paleo_bridge/start_bridge.sh &
		ensure the auto_heal.sh code is first and the start_bridge.sh is last

9. Restart Server
		Console output should read as:
	[PaleoVoIP] Auto-restart bridge is now running.
	[PaleoVoIP] Starting bridge...

Join Mumble, no mod required(hopefully?)
