# Qt Creator Remote Debug Window Program On Raspberry Pi
This page shows how to use Qt Creator to debug remotely on rpi and how to accelerate debugging. Youtube video.
Start an ssh session by executing following command.
```
ssh -X pi@192.168.6.218
```
Get system environment variable DISPLAY.
```
echo $DISPLAY
```
![image](https://github.com/MuyePan/QtCreatorRemoteDebugOnRpi/assets/136073506/9ef3f271-46be-45a2-85a2-3df690224861)

**DO NOT CLOSE THE SSH SESSION DURATION DEBUGGING.**

Goto **Projects**
Under **Run** section, on **X11 Forwarding** uncheck **Forward to local display**. 
Under Environment section, click Details to expand the environment option. Add following variables:
**DISPLAY** **localhost:10.0**
**LD_LIBRARY_PATH** **:/usr/local/qt6/lib/**
**XAUTHORITY** **/home/pi/.Xauthority**
You need to replace localhost:10.0 with what you got in above ssh session.
![image](https://github.com/MuyePan/QtCreatorRemoteDebugOnRpi/assets/136073506/54e28040-fabd-41b0-8179-a4df4b629504)

At this point, you can debug the program.

On **Edit** select **Preference**. Then goto **Debugger** select **GDB**. Uncheck **Use Automatic Symbol Cache**. In **Additional Startup Commands** append following code.
```
set solib-search-path /home/pmy/qt6/pi/lib:/home/pmy/qt6/pi/plugins/platforms:/home/pmy/qt6/pi/plugins/platforminputcontexts/:/home/pmy/qt6/pi/plugins/imageformats/
```
![image](https://github.com/MuyePan/QtCreatorRemoteDebugOnRpi/assets/136073506/32f48fbc-d0ca-4865-b8ef-5fb28ede8474)

