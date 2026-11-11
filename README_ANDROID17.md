# Attempting to backport LG Velvet 4G (`caymanslm`) 4.9.337 Kernel to run Android 17

**Status:** Untested / Work in Progress (Automated CI compile test active; hardware boot-testing pending).

## About this repository
I'm not a professional kernel developer, just an LG Velvet 4G (`LM-G910EMW` / `caymanslm`) owner trying to help keep this device alive!

Since `xbill9` successfully got Android 17 (LineageOS 24.0) running on the Pixel 3a (`sargo`) using Linux Kernel `4.9.337`, I cherry-picked his kernel compatibility backports onto our official `LineageOS/android_kernel_lge_sdm845` (`4.9.337`) tree.

## What's included so far
- **Version spoof:** Fake `uname` to `5.4.302` for `bpfloader`, `netbpfload`, and `netd`
- **Cgroups & BPF:** `cgroup_bpf` cloned socket reference & `cpuset` v2 behavior in v1 cgroup
- **SELinux:** Read and drop `netlink xperm` rules for modern policies
- **Memory & Syscalls:** `MAP_FIXED_NOREPLACE`, `MADV_WIPEONFORK`, `close_range()` (436), and `clone3` (435)
- **Capabilities:** `CAP_PERFMON`, `CAP_BPF`, and `CAP_CHECKPOINT_RESTORE`
- **Filesystem:** `EROFS` backport from Linux `5.4.302` enabled in `caymanslm` defconfigs

## Help & Testing
If you are a developer or builder with a build environment set up, feel free to check the Actions tab for build logs, test via temporary `fastboot boot`, or open PRs/issues with fixes!
