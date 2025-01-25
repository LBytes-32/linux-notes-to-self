# Linux Mint Notes
## Boot Error
If you encounter the following error...
```
Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image ??: Not Found
Failed to start MokManager: Not Found
Something has gone seriously wrong: import_mok_state() failed: Not Found
```
1. Open the boot drive files
2. Rename `\EFI\BOOT\grubx64.efi` to `mmx64.efi`
3. Should work now.

## Partition the hard drive (Old)
- Use Gparted to clear up free space.
- If you cannot remove your previously created swap partition, right click it, select "noswap", then you can remove it.
- Do NOT use Gparted to create the partitions. This will be done during installation.
- Do a manual install. DO NOT erase disk (obviouslly). DO NOT click "Install alongside windows" (As tempting as it may be).
- Create 4 partitions. (I allocated ~350 GB of free space next to my Windows 10 partition)
  - `Boot` (Select EFI...  allocate 5000 MB)
  - `Swap` (Select Swap... use size of ram: 8000 MB)
  - `Root` (Select EXT4... allocate 120000 MB... target `/`)
  - `Home` (Select EXT4... use rest of free space... target `/home`)

## Partition the hard drive (New PC Build)
- Select the SSD to install Linux. Create a GPT partition table if you haven't already done so.
- Please use the installer's partition tool. It is able to create EFI partitions. GParted cannot do this.
1. Create the BOOT partition (512 MB, Primary, EFI System Partition)
2. Create the SWAP partition (8192 MB, Primary, swap area)
3. Create the ROOT partition (150000 MB, Primary, EXT4 Journaling File System, mount `/`)
4. Create the HOME partition (Remaining MB, Primary, EXT4 Journaling File System, mount `/home`)
5. Begin installation. Wait for completion. Select "Continue Testing" instead of restarting.
6. Open Gparted. Name the new partitions for better organization.

## Installing NODE and NPM
- Do NOT install from the software repository.
- Navigate to NVM GitHub
- In the README, navigate to **Install & Update Script**.run this command (Version may deviate from the example, may require `sudo`).
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

## Linux Mint Customization
### General Settings
1. Set `settings > windows > behavior > special key to move and resize windows` to super.

### Horizontal OSD
1. Download the "Horizontal OSD" extension
2. Set "Width of OSD window" to 3
3. Set height to 0.2
4. Set "Size of level bar..." to 20
5. Disable "Show label"

### Start Menu
1. Download the "CinnVIIStarkMenu" Applet
2. Add the applet to the panel.
3. Disable "autoscrolling in application list"
4. Select "Use a custom icon and logo"
5. Select "Use menu animations"
6. Select "Use picture and user name"

### Theme
[VertexCinnamon98](https://www.cinnamon-look.org/p/2151806) is a lovely theme. How to install:
1. Download and decompress the GZ file.
2. Copy the folder to the `~/.themes` directory. If it doesn't exist, then create it.
3. Select `Settings > Themes > Advanced > Desktop > VertexCinnamon98`.
[Aero Cursor](https://www.cinnamon-look.org/p/999972) windows 7 mouse cursor.
1. Download and decompress.
2. Copy into the `~/.icons` directory. Create it if needed.
3. Select the new cursor. Be aware the icon is incorrect, but is named "Aero".
#### Edit GTK Theme
- go to `~/.themes/<theme>/gtk-3.0`
- backup `gtk.css` as `gtk-BACKUP.css`
- edit `gtk.css`

### Flatpak Cursor Issue
Flatpak applications may render the incorrect cursor. Follow these steps to resolve the issue. [Here is the reference post](https://www.reddit.com/r/linuxmint/comments/1hzk4br/cursor_themes_in_flatpak_fix/)
1. Copy the cursor folder to `~/.local/share/icons/`. (A copy will suffice. If the cursor files are already installed elsewhere, you may leave them be.)
2. Get the name of the cursor theme from `index.theme`.
3. Create the file `~/.Xresources` and append the contents `Xcursor.theme: <cursor name>`.
4. Run `xrdb -load ~/.Xresources` in the terminal.
5. Restart the flatpak application.
