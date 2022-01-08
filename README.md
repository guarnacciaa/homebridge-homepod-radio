
<p align="center">

<img src="https://github.com/homebridge/branding/raw/master/logos/homebridge-wordmark-logo-vertical.png" width="150">

</p>

# HomePod mini radio support

Homebridge accessory for streaming radio to Homepod mini

## Streaming radio to HomePod (mini)
Main idea is to stream to HomePod mini (or AppleTV) with the following command:
```
ffmpeg -i <streamUrl> -f mp3 - | atvremote --id <homepodId> stream_file=-
```

## Requirements 
- NodeJS (>=8.9.3) with NPM (>=6.4.1)
- ffmpeg
- pyatv

For Homepod device you need to specify the IP address of the device. 


## Usage Example:
```
{
    "platforms": [
        {
            "platform": "HomepodRadioPlatform",
            "name": "Homepod Radio",
            "model": "BBC - Radio 1",
            "homepodId": "F422F0103371",
            "radioUrl": "http://stream.live.vc.bbcmedia.co.uk/bbc_radio_one"
        }
    ]
}
```

## ffmpeg lib
- install ffmpeg
```
sudo apt-get install ffmpeg
```

## PyATV lib

For streaming to HomePod we are using pyatv (https://pyatv.dev). Setup instructions (for RaspberryPi)

- install python3  
```
sudo apt-get install python3
```
- install pip3
``` 
sudo apt-get install python3-pip
```
- install pyatv 
```
pip3 install pyatv
```
- make atvremote available for homebridge
```
sudo ln -s /home/pi/.local/bin/atvremote /usr/local/bin/atvremote
```

## Identify Homepod mini ID:
- run command:
```
atvremote scan
```
- from output select one of Identifiers:
```
       Name: HomePod
   Model/SW: HomePod Mini, tvOS 15.2
    Address: 192.168.1.7
        MAC: F4:22:F0:10:33:71
 Deep Sleep: False
Identifiers:
 - F4:22:F0:10:33:71
 - F422F0103371
```
## Stream URL format
The easieast would be to get streaming url from your favorite radio playlist (usually .m3u file)
Example For BBC Radio: https://gist.github.com/bpsib/67089b959e4fa898af69fea59ad74bc3


## TODO list
1. Volume control
2. Resume playback on Homebridge reboot?
