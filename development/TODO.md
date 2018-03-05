# TODO

- [ ] Add cordova-plugin-media-capture
- [X] Update to Cordova 8 and cordova-android 7
	- [X] ~This requres changing the XML~
- [ ] Fix cordova build warning 'loadLocalPlugins called twice with different search paths.Support for this is not implemented.  Using previously cached path.'
- [ ] Ensure development branch is using local path (if possible, lol) *
- [ ] Scrub *my* web client ID and client ID from the dev build *
- [ ] Fix Android 'connecting to device error' 

\* Or just don't commit the platform additions as each dev must do that themselves

---

Error: 

```
file:///android_asset/www/js/googleDrive.js Failed to load resource: net::ERR_FILE_NOT_FOUND
cordova.js:1470 Uncaught Error: Module cordova-plugin-jc-googledrive.GoogleDrive does not exist.
cordova.js:1224 deviceready has not fired after 5 seconds.
cordova.js:1217 Channel not fired: onPluginsReady
cordova.js:1217 Channel not fired: onCordovaReady
```

Solution:

```
cd www 
mkdir js
ln -s googleDrive.js js 
ls
  googleDrive.js js
ls js 
  googleDrive.js
file js/googleDrive.js
  js/googleDrive.js: broken symbolic link to googleDrive.js
rm js/googleDrive.js
cd js 
ln -s googleDrive.js ../googleDrive.js 
  ln: ../googleDrive.js: File exists
ls
ln -s ../googleDrive.js 
ls
  googleDrive.js
file googleDrive.js 
  googleDrive.js: ASCII text
less googleDrive.js 
```

---

The Android Persistent storage location now defaults to "Internal". Please check this plugin's README to see if your application needs any changes in its config.xml.

If this is a new application no changes are required.

If this is an update to an existing application that did not specify an "AndroidPersistentFileLocation" you may need to add:

      "<preference name="AndroidPersistentFileLocation" value="Compatibility" />"

---


