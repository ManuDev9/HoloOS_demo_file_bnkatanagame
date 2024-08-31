
This is a version of HoloOS with Bodynodes support which enables the control of objects in 3D environments with Bodynodes motion capture sensors.

The game is currently in:
- GUI_TK/bnkatanagame

- Inside there is:
  - main.py: the file that runs the 3D environment
  - body-nodes-host: which is a submodule contaning all the code to collect and return capture data

The Bodynodes system is composed by two actors:
- one or more Nodes and
- a Host

The Nodes and Host communicate over a network, that can be:
- Wifi or
- Bluetooth

At the moment the main.py file is making use of the Wifi Host implementation via this line:
    import bnwifibodynodeshost as bodynodeshost

If you want to make use of a Bluetooth Host implementation use the following line:
    import bnbluetoothbodynodeshost as bodynodeshost

Wifi tends to be easier to use that's why I initially set the game in this way. In fact, please have a look at some usefull instructions in order to
enable Bluetooth on your Linux machine or Raspberry.

From:
https://github.com/ManuDev9/body-nodes-host/blob/master/modules/pythonlib/bnbluetoothbodynodeshost.py

 sudo apt-get update
 sudo apt-get install libbluetooth-dev
 sudo apt-get install python3-bluez
 pip install pybluez
 bluetoothctl show
              power on
              power off
              discoverable on
              pairable on
              pair

 rfkill list bluetooth
 Name: Pixel A - Address: 13:95:2G:61:6P:C6
                 pair 13:95:2G:61:6P:A6
                 connect 13:95:2G:61:6P:C6
                 info 13:95:2G:61:6P:C6
 UUID: Serial Port              (00001101-0000-1000-8000-00805f9b34fb)

It is best to first run the mobile app, and then pair it to propertly discover the UUID Serial Port
otherwise it might be seen. NOTE: This happens ONlY the first time the Host pair to the Node


Depending on which communication channel you choose for the Host, you need to have Nodes that make use of the same channel. You need a Wifi or Bluetooth
Node implementation. You can find them here:
    https://github.com/ManuDev9/body-nodes-sensor

The simplest one to use is the Bodynodes Sensor App, which is an Android app that makes your smartphone act as a Bodynodes Sensor via Wifi or Bluetooth.
    https://github.com/ManuDev9/body-nodes-sensor/tree/master/android/BodynodesSensor

In here you can find/download/install a working APK with the game:
    https://github.com/ManuDev9/body-nodes-sensor/blob/master/android/BodynodesSensor/release/BodynodesSensorApp_20240831.apk

Once you open the app, just make sure in Settings that:
- Multicast for Wifi is "BN"
- Bodypart is "Katana"
- And that you selected the Connection type you want, Wifi or Bluetooth
- Then tap on Save

Afterwards you can start the app by pressing "Start" 















