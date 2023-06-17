# Debug Qt Widgets/Quick Application on RPI remotely with Qt Creator
This page shows how to use Qt Creator to debug Qt Widgets Application remotely on rpi and how to accelerate debugging. 

Click the follow image to view this tutorial on Youtube.

## Make debugging work
Goto **Projects**
Under **Environment** section, click **Details** to expand the environment option. Add following variables:
- **LD_LIBRARY_PATH** **:/usr/local/qt6/lib/**
- **XAUTHORITY** **/home/pi/.Xauthority**

![image](https://github.com/MuyePan/QtCreatorRemoteDebugOnRpi/assets/136073506/b4934a58-6db7-421e-a96e-36f7fe23aa85)

## Accelerate remote debug
On **Edit** select **Preference**. Then goto **Debugger** select **GDB**. Uncheck **Use Automatic Symbol Cache**. In **Additional Startup Commands** append following code.
```
set solib-search-path /home/pmy/qt6/pi/lib:/home/pmy/qt6/pi/plugins/platforms:/home/pmy/qt6/pi/plugins/platforminputcontexts/:/home/pmy/qt6/pi/plugins/imageformats/
```
![image](https://github.com/MuyePan/QtCreatorRemoteDebugOnRpi/assets/136073506/32f48fbc-d0ca-4865-b8ef-5fb28ede8474)

**/home/pmy/qt6/pi** is the binary generated by cross compiling Qt6 for rpi. This link https://github.com/MuyePan/CrossCompileQtForRpi shows how to cross compile Qt6.5.1 
for rpi step by step.

