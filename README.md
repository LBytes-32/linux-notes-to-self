# Linux Mint Notes
## Partition the hard drive
- Use Gparted to clear up free space.
- If you cannot remove your previously created swap partition, right click it, select "noswap", then you can remove it.
- Do NOT use Gparted to create the partitions. This will be done during installation.
- Do a manual install. DO NOT erase disk (obviouslly). DO NOT click "Install alongside windows" (As tempting as it may be).
- Create 4 partitions. (I allocated ~350 GB of free space next to my Windows 10 partition)
  - `Boot` (Select EFI...  allocate 5000 MB)
  - `Swap` (Select Swap... use size of ram: 8000 MB)
  - `Root` (Select EXT4... allocate 120000 MB... target `/`)
  - `Home` (Select EXT4... use rest of free space... target `/home`)

## Installing NODE and NPM
- Do NOT install from the software repository.
- Navigate to NVM GitHub
- In the README, navigate to **Install & Update Script**.run this command (Version may deviate from the example, may require `sudo`).
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```
