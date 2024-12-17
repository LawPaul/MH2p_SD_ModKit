# MH2p SD ModKit
Free ModKit that allows for modifying the MH2p unit used in some Volkswagen AG vehicles using only an SD card.
## License
 - This file is part of MH2p_SD_ModKit, licensed under CC BY-NC-SA 4.0.
 - https://creativecommons.org/licenses/by-nc-sa/4.0/
 - See the LICENSE file in the project root for full license text.
 - NOT FOR COMMERCIAL USE
## Compatible vehicles
Please let me know of additional vehicles to add to this list.
 - 19-24 Porsche Macan
## Necessary hardware
 - SD card
 - Computer that can connect to SD card
## ModKit setup
 - format SD card as FAT32
 - extract entire contents onto SD card
 - Windows notes:
     - right click the SD card, choose "Format", select "FAT32" from "File System," and choose "Start".
 - macOS notes:
     - use the built-in Disk Utility app to format the SD Card to FAT32: Applications > Utilities > Disk Utility.
     - hidden files starting with "." are created automatically.
     - If these are present, you will see a more than one manifest file found error when trying to run the initial update through the red engineering menu. To get around this, you must delete these hidden files prior to removing the SD Card.
     - If you don't see the hidden files, press Command then Shift then . (period) to display them (they will show up slightly greyed out)
     - Delete the files (they all start with a period).
     - Remove the SD Card from the port physically. Do not use the eject function on finder; using the eject function adds the files in right before it is ejected.
## Mods setup
 - note: this does not include any mods, they must be downloaded separately
 - download mods and extract them into the `/Mods` folder
 - to have the mod ready for install:
     - ensure `install.sh` exists
 - to have the mod ready for uninstall:
     - rename `install.sh` to `_install.sh`
     - rename `_uninstall.sh` to `uninstall.sh`
## Vehicle installation
 - start vehicle
 - insert SD card
 - update installs automatically: MH2p will reboot a few times and show some red engineering menu pages
 - when update is done installing, a prompt will say "Please remove update media"
 - remove SD card
 - MH2p will reboot into normal mode with mods installed/uninstalled
 - on PC, can check SD card `/Logs` folder which has logs from each mod being installed
 ## Mod development
 - each mod should be self-contained in its own folder `/Mods/[modname]`
 - each mod should include `install.sh` and `_uninstall.sh`
 - mods are launched by `/Data/MMX2P_POSTSCRIPT.script_2021623-0210/0/mod.sh`
 - mod output is logged to `/Logs/[modname].log`
 - if `install.sh` is present, it is run
 - if `install.sh` is not present and `uninstall.sh` is present, it is run
 - users can choose to install or uninstall by changing which file name starts with "_"
 - `mod.sh` exports a few userful variables:
     - `mediaPath`: path to SD card ex: `/fs/sdb0`
     - `modPath`: path to mod's folder ex: `/fs/sdb0/Mods/[modname]`
     - `mod`: name of mod (same as mod's folder name) ex: `[modname]`
## How it works
 - the ModKit is a valid checksummed and signed update for MH2p
     - I discovered checksum and signing methods through reverse engineering MH2p binaries
 - the update runs `mod.sh` which runs scripts under `/Mods/` that are not checksummed or signed
 - this allows easier development and installation of mods
## Credits
 - UncleMacan ([Macan Forum](https://www.macanforum.com/members/unclemacan.173728/)): worked together on Porsche CarPlay true fullscreen; wanting an easier installation method got me started making SD ModKit
 - lprot ([GitHub](https://github.com/lprot), [DRIVE2](https://www.drive2.ru/users/lprot/)): general platform knowledge, MH2p Toolkit
 - MacanPWR ([Macan Forum](https://www.macanforum.com/members/macanpwr.174775/)): macOS SD card notes
 - [Ghidra](https://github.com/NationalSecurityAgency/ghidra): reverse engineering MH2p binaries
 - [Recaf](https://github.com/Col-E/Recaf): reverse engineering & modifying for CarPlay true fullscreen
 - "experts" selling their "services": motivation to make CarPlay true fullscreen & SD ModKit available to all for free
 ## Contact
 - [GitHub](https://github.com/LawPaul)
 - [Macan Forum](https://www.macanforum.com/members/carmines.174281/)
 - [DRIVE2](https://www.drive2.ru/users/lawsen/)
 - [Discord](https://discordapp.com/users/lawsen5734)
