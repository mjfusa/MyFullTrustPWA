## My FullTrust PWA

This demonstrates a Progressive Web App with the follow components:

1. WRCBackgroundTasks (Windows Runtime Compoment)
Contains the following background tasks:
	
   a. Pre-Install
    
    b. Timer
    
    c. Connected Session
    
    d. Application
    
2. My PWA - Simple PWA app host local content
This registers the background tasks. See js/main.js

3. LauncherWin32 - This is a full trust app that launches 'MyPWA' from the Preinstall task using the API 
```
FullTrustProcessLauncher.LaunchFullTrustProcessForCurrentAppAsync(); 
```
This was necessary since a requirement was to launch from pre-install - before the app protocol is registered at install time.

The app is Full Trust, with a custom protoco and full trust process defined. See package.appxmanifest.

Note addition of <build> section to appxmanifest, this was workaround to a problem with full trust apps require special build handling - this is done if the app is packaged with a Desktop Packaging Project - however, PWAs can't be adding to packaging projects since they require only projects with EXE output to be added.
