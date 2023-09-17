# CS2Downloader-Manifests
Using the following method you can download Counter-Strike 2 game files from official steam servers

1. Manifest zip files shared by me will contain 5 files, these are.
   - 2347770 - Counter-Strike 2 Game Files
    - 2347771 - Counter-Strike 2 Windows Binaries
     - 2347779 - Counter-Strike 2 Workshop Tools
      - depot_keys.json - Used to decrypt chunks downloaded


# ![](https://img.icons8.com/?size=60&id=DWiebo2M1Bbt&format=svg) How it work :
**We will be using steamctl to download and verify game files using depot decryption keys and decrypted manifest files provided under this thread. To get started you will need to install python and install steamctl using following command**


``pip install steamctl``

Download latest manifest zip and extract it. Copy depot_keys.json to %LocalAppData%\steamctl\steamctl\

##
**Download Game Files**

Now open command prompt or powershell and cd to the directory where you extracted manifest zip. Run following commands one by one to download all 3 game depots


``steamctl depot download -f .\730_2347770_7394304315934590367 -o ./depots --skip-licenses --skip-login``

``steamctl depot download -f .\730_2347771_3031085382770375306 -o ./depots --skip-licenses --skip-login``

``steamctl depot download -f .\730_2347774_4260986158965787628 -o ./depots --skip-licenses --skip-login``

This would download game files in folder named depots. In order to play the game offline you will need to patch client.dll placed under game\csgo\bin\win64\.

**There are multiple patchers floating you can use to patch client.dll**
##
**Download Workshop Tools**

From the same command prompt execute following command to download Counter-Strike 2 Workshop Tools

``steamctl depot download -f .\730_2347779_5528370932775793682 -o ./depots --skip-licenses --skip-login``

##
**Verify Game File Integrity**

You can verify game file integrity using following commands check if something is missing or corrupted. I don't think we can selectively download corrupted files using steamctl, you can look at the documentation and report if I missed it.

``steamctl depot diff -f .\manifests\730_2347770_7394304315934590367``

``steamctl depot diff -f .\manifests\730_2347771_3031085382770375306``

``steamctl depot diff -f .\manifests\730_2347774_4260986158965787628``

``steamctl depot diff -f .\manifests\730_2347779_55283709327757936826``

Ideally use this command where you have the "game" folder for example

``PS C:\> cd "C:\Program Files (x86)\Steam\steamapps\common\Counter-Strike Global Offensive"``

``PS C:\Program Files (x86)\Steam\steamapps\common\Counter-Strike Global Offensive> steamctl depot diff -f C:\manifests\730_2347770_7394304315934590367``

## want to update game every new update?

Well in that case you have to find someone who has access to Beta and ask them to share the decrypted update manifest file. These files can be found under C:\Program Files (x86)\Steam\depotcache\<depotid>_<manifestid> (Steam installation path)

For obtaining manifest file using steamctl run following command

``steamctl -l debug depot info -a <appid> -d <depotid> -m <manifestid>``

