This file contains high-level info about how XwalkDriver works.

XwalkDriver is an implementation of the WebDriver standard. Part of code is
ported from ChromeDriver.

=====How To=====
For Linux xwalk:
(1) Build XwalkDriver by building the 'xwalkdriver' target and get an executable
binary in the build folder named 'xwalkdriver'.

(2) Build 'xwalk' target, install it in "/opt/crosswalk" or working path of
'xwalkdriver'.

(3) Use following python instructions to do a basic test.

$ export PYTHONPATH=<THIS_DIR>/server:<THIS_DIR>/client
$ python
>>> import server
>>> import xwalkdriver
>>> cd_server = server.Server('/path/to/xwalkdriver/executable')
>>> driver = xwalkdriver.XwalkDriver('http://127.0.0.1:9515')
>>> driver.Load('http://www.google.com')
>>> driver.Quit()
>>> cd_server.Kill()

For Android xwalk:

(1) Build XwalkDriver by building the 'xwalkdriver' target and get an executable
binary in the build folder named 'xwalkdriver'(Details referred to ../README.md).
Or download the binary from
    https://github.com/crosswalk-project/crosswalk-web-driver/bin

(2) Pakage your app by execute command
    python make_apk.py --package=YOUR_APP_PACKAGE_NAME --manifest=YOUR_APP_PATH/manifest.json \
      --arch=YOUR_DEVICE_ARCH --enable-remote-debugging

(3) Install your apk to device.

(5) Run xwalkdriver binary.
    $./xwalkdriver
    If xwalkdriver runs on a remote server, you can authorize security clients on where

(6) Execute following commands to test:
$ python
>>> import xwalkdriver
>>> driver = xwalkdriver.XwalkDriver('http://127.0.0.1:9515', android_package='', android_activity='')
>>> driver.quit()

