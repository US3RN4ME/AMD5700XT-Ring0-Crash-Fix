# AMD RX 5700 XT Ring0 Crash Fix for Linux
Guide for troubleshooting.

**Things to check first:**
- GPU must have 2 dedicated power lanes, be sure there is not a loose cable.
- Check GPU fans for dust.

**STEPS TO FOLLOW (CoreCtrl):**
- Replace the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub with: `GRUB_CMDLINE_LINUX_DEFAULT='quiet splash amdgpu.noretry=0 amdgpu.lockup_timeout=0 iommu=pt amdgpu.gpu_recovery=1 amdgpu.runpm=0 amdgpu.mcbp=0 amdgpu.ppfeaturemask=0xf7fff'`
- Run `sudo update-grub` and reboot.
- Now download [CoreCtrl](https://gitlab.com/corectrl/corectrl) and the file **FIX.ccpro** listed in this repository.
- Follow [this guide](https://gitlab.com/corectrl/corectrl/-/wikis/Setup) to setup CoreCtrl.
- Import **FIX.ccpro** in CoreCtrl's profile list.
- Modify the fan curve to your liking and apply.

**STEPS TO FOLLOW (LACT):**
- Replace the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub with: `GRUB_CMDLINE_LINUX_DEFAULT='quiet splash amdgpu.noretry=0 amdgpu.lockup_timeout=0 iommu=pt amdgpu.gpu_recovery=1 amdgpu.runpm=0 amdgpu.mcbp=0 amdgpu.ppfeaturemask=0xf7fff'`
- Run `sudo update-grub` and reboot.
- Now download [LACT](https://github.com/ilya-zlobintsev/LACT) and the file **config.yalm** listed in this repository.
- Replace the current **config.yalm** file to the one downloaded from this repository in /etc/lact/
- Start LACT daemon with `sudo systemctl enable --now lactd` and add it to boot with `sudo systemctl enable lactd` (Find the equivalent command for your INIT system)
- Start LACT with GUI and change your profile to "Altered".
- Modify the fan curve to your liking and apply.

**For more information check [this Reddit thread](https://www.reddit.com/r/linuxquestions/comments/1lbbiwm/amd_radeon_rx_5700_xt_irregular_crashes_only/).**

**I followed [this undervolting guide](https://www.reddit.com/r/overclocking/comments/16gmhhk/undervolting_rx_5700_xt_a_deep_dive_into/) for the guide.**
