## Guide to Install MK11 on Linux

1. Install Steam on your Linux machine : https://store.steampowered.com

2. Install and activate the Latest version of Proton-GE-Custom on Steam : https://github.com/GloriousEggroll/proton-ge-custom/releases/latest

3. Now you can install MK11, go to your Steam library and click on the Mortal Kombat 11 install button

4. Exit the Steam and run the game with this command just for the first time to see Proton logs ( it may take a while ) and then exit the game

```sh
steam steam://run/976310
```

3. Use this fix for desync issues in online mod : https://github.com/ValveSoftware/Proton/issues/2594#issuecomment-833121204

4. Install mf-install with following command

```sh
git clone https://github.com/z0z0z/mf-install.git
cd mf-install
WINEPREFIX="/home/<username>/.steam/steam/steamapps/compatdata/976310/pfx" PROTON="/home/<username>/.steam/steam/compatibilitytools.d/Proton-VERSION" ./mf-install.sh -proton
```

7. Run the game with Steam launcher

Enjoy!

## Intel Performance Support

if you use intel CPU, do the following :

```sh
sysctl -n dev.i915.perf_stream_paranoid
```

if the output is `1`, you can change it to `0` with the following command :

```sh
sudo crontab -e
# add this line at the bottom or end of the file
@reboot /sbin/sysctl -q -w dev.i915.perf_stream_paranoid=0
```

Reboot your machine, and you should be good to go

## Game crash at the start

First, make sure that the Shader pre-caching is "off"
also, remove the MK11 shader cache folder

```sh
rm -rf ~/.steam/steam/steamapps/shadercache/976310
```

I do not have a permanent solution for this, but reboot your machine and try again if this happens.

It works for me!

## Upgrade Proton

if you want to upgrade Proton, be sure to remove the current MK11 wine folder before that :

```sh
rm -rf ~/.steam/steam/steamapps/compatdata/976310
```
