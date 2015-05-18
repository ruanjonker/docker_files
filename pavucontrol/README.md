

1. Configure pulseaudio to listen on tcp
=============

```bash
#On your host machine:

sudo apt-get update && apt-get install -y paprefs

#Launch PulseAudio Preferences, go to the "Network Server" tab, and check the "Enable network access to local sound devices" and "Don't require authentication" checkboxes
paprefs

#NOTE: You might have to restart for the above to take effect, to check run pax11publish

pax11publish

#Should yield output like ...

#Server: {d4fcbcafd9a9d96eda56bf9d551041fd}unix:/run/user/1000/pulse/native tcp:YOUR_HOST_NAME:4713 tcp6:YOUR_HOST_NAME:4713
#Cookie: c1d4b7d7e34a68fb0ca470b3346c1aff6e588fece590574273bf119b968dbe..... very long hex string

#Where YOUR_HOST_NAME is the set to the output of `hostname -s`


```

2. Build your docker image
=============

./build


3. Run it !
============

./run




