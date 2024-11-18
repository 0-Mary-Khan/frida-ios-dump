# frida-ios-dump
Pull a decrypted IPA from a jailbroken device using SSH on Linux


## Usage

 1. Use Linux (or WSL).
 2. (Optionally) Enter into a virtual environment:
```bash
sudo apt install python3-venv
python3 -m venv .venv
source .venv/bin/activate
```
 3. Install requirements:
```bash
python3 -m pip install -r requirements.txt --upgrade
```
 4. Enable Frida server on the device.
 5. Enable root SSH access to the device.
 6. Dump the app:
```bash
python3 dump.py -H '<ssh_host>' -K '<ssh_key>' '<app_name>|<app_identifier>'
```

## Example
```bash
python3 dump.py -H '192.168.0.100' -K 'id_rsa' 'sg.vp.UnCrackable1'
Start the target app sg.vp.UnCrackable1
Connected!  Tunnel open ('127.0.0.1', 36506) -> ('192.168.0.100', 22) -> ('127.0.0.1', 27042)
Dumping UnCrackable1 to /tmp
start dump /private/var/containers/Bundle/Application/FF2BFE6D-3B08-4E8B-BC1C-E6D89DC60A78/UnCrackable Level 1.app/UnCrackable Level 1
UnCrackable Level 1.fid: 100%|███████████████████████████████████████████████████████████████████| 72.0k/72.0k [00:00<00:00, 317kB/s]
AppIcon-176x76@2x~ipad.png: 415kB [00:01, 392kB/s]
0.00B [00:00, ?B/s]Generating "UnCrackable1.ipa"
```

## Support

Python 3.x


### issues

If the following error occurs:

* causes device to reboot
* lost connection
* unexpected error while probing dyld of target process

Please retry or open the application before dumping.