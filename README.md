# openfin-embed-air

Examples of Air windows embedded in OpenFin windows.  Each Air window must have an unique name, set by stage.nativeWindow.title, in order for embedding to work.

# Run the example
1. start a web server in web directory on localhost:8080

2. go to lib/ and run OpenFinEmbed.exe.  If certificate error appears, older version of the app needs to be uninstalled from "Programs and Features".

# Build the project

This project is created and built with IntelliJ IDEA 2017.1.5 with following settings: <br>
Target Platform: Desktop <br>
Output Type: Application <br>
Main Class: OpenFinEmbed <br>
Output Filename: OpenFinEmbed.swf <br>
Custom Template: OpenFinEmbed-app.xml <br>
Flex/AIR SDK:  flex_sdk_4.6 <br>
Component set: Spark + MX <br>
Dependencies:  lib/OpenFinAirAdapter-6.0.1.swc (Merged), lib/OpenFinAirNativeExtension-6.0.1.ane <br>

# Build the project

OpenFinEmbed.mxml is an example to demonstrate how to embed Air windows into OpenFin windows so OpenFin windows provide chrome styled with css.  It also supports Snap&Dock of windows, provided by https://github.com/openfin/snap-and-dock.

1. Files
web/app.json:  app manifest for OpenFin Runtime. <br>
web/Launcher.html:  first app launched from app.json by OpenFin Runtime.  It sets up DockingManager. <br>
web/AirChrome.html: OpenFin window that captures Air windows and provide chrome to Air windows. <br>

2. Launch Runtime from OpenFinEmbed.mxml

    ~~~javascript
    var cfg:RuntimeConfiguration = new RuntimeConfiguration("Flex Test App");
    cfg.appManifestUrl = "http://localhost:8080/app.json";
    cfg.onConnectionReady = onConnectionReady;
    cfg.onConnectionError = onConnectionError;
    cfg.onConnectionClose = onConnectionClose;
    cfg.connectionTimeout = 15000;
    runtimeLauncher = new RuntimeLauncher(cfg);
    ~~~

3. Capture Air window

btn_captureHandler function in OpenFinEmbed.mxml configures parameters for capturing an Air window by an OpenFin window.  Each Air window must have an unique title, set by stage.nativeWindow.title.

4. Snap and Dock

Moving 2 windows close should trigger snap&dock.

