# SPDTools (DroidYisky)
The Guide made for the people who wants to use Spreadtrum tools without PC, but has droidspace compatibility, USB Hub, Root Access Instead

# Disclaimer
I am not responsible to anything that bricks your phone, what I did is make this guide and its not my duty to update the tool because I don't have the necessary tools to decompile the binaries to do so. And if you point your finger to me I'll laugh at you and there's nothing you can do but feel ashamed to yourself. Applies to every people you blame, and its fully not their duty to help to what responsibility you had. They can only help when you are having problems and need assistance

#### You must have...
 - Droidspace support
 - Knowledge
 - USB Hub or Type C to Type C
 - 50% Battery
 - Container already setup
#### Once you have them all, you can proceed to the installation
Open Terminal and type this commands below
```bash
apt update && apt upgrade -y
```
Wait until it finishes, then install the drivers:

```bash
sudo apt-get install build-essential libusb-1.0-0-dev git wget curl unzip zip
```
Then you must gather the termux version for this guide. Paste this commands on the terminal and click enter.
```bash
curl -L -O https://github.com/Seuj09/Spd_dump_termux/releases/download/Release/spreadtrum_flash_termux_arm64.zip
unzip spreadtrum_flash_termux_arm64.zip
cd spreadtrum_flash_termux
```
Then paste this commands after waiting to complete the download
```bash
chmod +x spd_dump chsize gen_fdl1-dl gen_spl-unlock gen_spl-unlock-legacy \
pacextractor unpac menu.sh extrac.sh misc-fastbootd.bin misc-wipe.bin
```
You can launch the menu.sh by typing the command
```bash
./menu.sh
```
## Limitations

- **`spdfl` is not included.** It is a closed-source x86-64 binary with no
  public source, so it cannot run on arm64. Use `./menu.sh` instead — the menu
  drives `spd_dump` directly.
- **`pacextractor` and `unpac` are still x86-64.** They have no public source,
  so they could not be rebuilt for arm64. They are only used by `extrac.sh` for
  PAC-archive extraction; the main flash/unlock flow does not depend on them.
- **V35 device folders are empty.** The new tool's per-device directories ship
  without `fdl*.bin` firmware, so device coverage is unchanged from the original
  tool. If your device isn't listed, you'll need to supply its `fdl` firmware
  yourself.

## Credits

- **[TomKing062](https://github.com/TomKing062/CVE-2022-38694_unlock_bootloader)** —
  the open-source CVE-2022-38694 unlock-bootloader toolchain, source of the
  arm64 `spd_dump`, `chsize`, `gen_fdl1-dl`, `gen_spl-unlock`, and
  `gen_spl-unlock-legacy` binaries and the unlock method.
- **[Massatriof16](https://github.com/Massatriof16/recovery-collections)** —
  the Spreadtrum Flash V35 tool, which provided the tool layout used here.
- The **Spreadtrum/Unisoc reverse-engineering community** for the underlying
  flashing research and `fdl` firmware.
- **[Seuj09](https://github.com/Seuj09)** - Some words ain't mine btw
