# robovac30c_homeassistant
Guide: How to connect the Eufy Robovac 30c To home assistant


## Update January 2025:
Just use this HACS component, it works out of the box: https://github.com/CodeFoodPixels/robovac


## Old Instructions
After few hours wasted on google with various information, I got it working, hopefully I can save you some time.
The original Eufy plugin is not working, you need a custom plugin, the one from mitchellrj seems to work.
Also, it seems the 30c has a different API connection so the acces_token is not available via curl anymore, but this old apk of the app shows it! no need to sniff or install other stuff.

How to:
- Go to your home assistant folder and create a "custom_components" folder
- Install the following component into it https://github.com/mitchellrj/eufy_robovac
- NOTE! Rename the folder eufy_robovac in "eufy_vacuum"
- NOTE2! In order to make it work with newer versions of HomeAssistant,  you have to create a manifest.json file as described in https://github.com/mitchellrj/eufy_robovac/issues/29
- download this version of the eufy app on an android device: https://www.dropbox.com/s/bcwy6iqchydgexc/EufyHome_2.4.0_vevs.apk.zip?dl=0 (I don't know who is the owner and if the app is legit, found it here https://www.reddit.com/r/homebridge/comments/hda5td/easy_way_to_obtain_localkeydevid_for_eufy_vacuums/)
- Select your robot and select settings, devive id and license key are there.

- Edit the configuration.yaml as following:

```yaml
eufy_vacuum:
  devices:
  - name: Robovac
    address: 192.168.x.x
    access_token: 
    id: 
    type: T2118
```

- restart home assistant and you are good to go!
