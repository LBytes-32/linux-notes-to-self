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

## Installing NODE and NPM
- Do NOT install from the software repository.
- Navigate to NVM GitHub
- In the README, navigate to **Install & Update Script**.run this command (Version may deviate from the example, may require `sudo`).
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```
