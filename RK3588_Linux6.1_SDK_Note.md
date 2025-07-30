# RK3588 Linux6.1 SDK Note

---

**Contents**

[TOC]

---

## rk3588_linux6.1_release_v1.3.0_20250620.xml Note

### Summary of Major Updates

- Optimize SDK compilation environment checks and prompts
- Optimize Yocto configuration mechanism to facilitate custom development for small chips
- Optimize frecon virtual terminal mechanism
- Optimize root file system overlay mechanism
- Optimize recovery configuration mechanism
- Support scenarios with standalone Wi-Fi only (no Bluetooth)
- Refactor rkscripts for greater generality
- Add SDK security updates and support/documentation related to CVEs
- Add Yocto and Debian support for chips without a GPU
- Add Debian 12 Wayland system support
- Add more environment checks and prompt messages
- Upgrade Chromium to the latest LTS version R132
- Buildroot supports the mimalloc memory allocator
- Weston supports hardware mouse scaling
- Optimize Weston boot speed
- Buildroot supports configuration of serial port login methods under systemd
- Update ADB to a newer version to support more features

### Major Issues Fixed in the SDK

- Fix abnormal functionality of the USB gadget under Debian

- Upgrade support for 8-bit ECC drivers of GD5F2GM7RxG, GD5F2GM7UxG, and GD5F1GM7UxG SPI NAND components, and resolve issues with abnormal device boot

- Resolve the issue where devices cannot be recognized during PCIe sleep/wake cycles

- Fix reference counting issues in the kernel-6.1 vicap module related to sensor power calls

- Fix system hangs caused by anomalies in the JPEG decoder

- Fix intermittent pauses and freezes during GST MPP hardware decoding in specific scenarios

- Fix abnormal UVC hotplug behavior

- Fix abnormal Bluetooth sleep/wake issues under Debian

- Fix intermittent "failed to online" errors of big-core CPUs after logic non-power-off sleep/wake for the rk3588 + rk806 + rk860 power supply solution

- Fix display anomalies caused by premature release of the display clock during the kernel logo stage

- Fix system crashes triggered by PCIe function drivers calling platform reset functions

- Fix system hangs caused by anomalies in the JPEG decoder (duplicate entry)

- Fix issues where devices with GD5F1GM7UEYIGR SPI NAND components fail to boot normally if transported/stored for multiple months

### Update Status of SDK Components

| **Module**                    | **Content**                                                  |
| ----------------------------- | ------------------------------------------------------------ |
| Security Updates              | 1. **Linux Kernel**: Security update for Kernel 6.1 from 6.1.99 to 6.1.118. For details, refer to the official release [linux-cve-announce](https://lore.kernel.org/linux-cve-announce/).<br/>2. **Buildroot**: Upgraded to [Buildroot 2024.02](https://git.busybox.net/buildroot/plain/CHANGES?id=2024.02).<br/>3. **Yocto**: Security updates applied; current Yocto 5.0 version is 5.0.8. For more information, see [release-notes-5.0.8](https://docs.yoctoproject.org/migration-guides/release-notes-5.0.7.html).<br/>4. **Debian**: Debian 12 security updated to version 12.12. Details can be found in [Debian12.12](https://www.debian.org/News/2025/20250315). |
| Buildroot Update              | 1. meson package supports multi-threaded compilation<br/>2. weston fixes several anomalies under pixman-renderer<br/>3. weston fixes rk3399 gl-renderer anomalies<br/>4. gstreamer upgraded to 1.24<br/>5. libcamera upgraded to 0.5.0<br/>6. weston upgraded to 14.0.2<br/>7. Fix dropbear SSH connection anomalies<br/>8. Support using busybox bash to save space<br/>9. Support openssl rootfs encryption<br/>10. Support nvme storage secure boot<br/>11. Update chromium from r126 to 132.0.6834.83<br/>12. buildroot supports mimalloc memory allocator<br/>13. weston supports hardware mouse scaling and optimizes boot speed<br/>14. buildroot supports systemd serial port login configuration<br/>15. Update LVGL to support new features<br/>16. GLIBC upgraded from 2.38 to 2.41<br/>17. GCC upgraded from 12.4 to 13.3<br/>18. Update third-party packages such as libdrm, libcamera, xenomai, dhcpcd<br/>19. Add product feature configurations for RK3576 Cluster, DV, CVR, etc.<br/>20. Add chip configuration support for RV1126B |
| Debian Update                 | 1. Add wayland system<br/>2. Add rv1126b Debian branch support<br/>3. Fix GPU horizontal issues on g24p0-9<br/>4. Fix USB gadget function anomalies on Debian<br/>5. Update RK hardware acceleration packages (rknpu/rkaiq/rga/xserver/mpp/chromium, etc.)<br/>6. Fix BT sleep-wake anomalies on Debian |
| Yocto Update                  | 1. Configure chip-specific compilation parameters to optimize performance<br/>2. Add common chip configurations for easier support of new chips<br/>3. Fix local repository source synchronization anomalies during compilation<br/>4. Fix chromium hardware encoding anomalies<br/>5. Fix rk3576 glmark2-es2-wayland anomalies<br/>6. Fix individual board-level configuration issues<br/>7. Update Yocto 5.0.8 LTS<br/>8. Upgrade chromium to 132<br/>9. Add meta-lts-mixins repository<br/>10. Add rockchip-custom configuration requirements |
| RTOS Update                   | 1. Add RV1126 MCU AMP support<br/>2. Add RK3568 Kernel 6.1 AMP support<br/>3. Add RK3568 HAL 64-bit support<br/>4. Add RK3576/RK3588 MCU AMP support<br/>5. Add RK3576/RK3588 AP AMP support |
| LVGL Update                   | 1. lvgl9 supports automatic drawing unit creation based on CPU count<br/>2. lvgl9 supports mimalloc<br/>3. lvgl9 optimizes software scaling performance<br/>4. lvgl9 drm supports specifying connector and plane<br/>5. lvgl9 adds asynchronous delay call interface<br/>6. lvgl8 fixes sdl draw line crash issue<br/>7. Fix some errors in Config<br/>8. SDL supports transparent windows |
| RKIPC Update                  | 1. Audio adds support for mp3, vqe\aed\bcd algorithms<br/>2. rk3576 dv app: Adds slow-motion, time-lapse, horizon stabilization modes; optimizes stabilization effects. Adds album and advanced options; optimizes UI display. Fixes several crash issues.<br/>3. Adapts to rv1126b's latest ISP\FEC\VPSS\AIISP hardware; supports HDR\OSD\NPU\VENC\VO\IVS functions<br/>4. rv1126b adds monocular, binocular, and DV modes<br/>5. Supports RV1126B DV product-related functions<br/>6. RV1126B web UI supports FEC, rotation, sub-code stream smart features, UVC NV12 support, etc. |
| MPP Update                    | MPP updated from v1.0.8 to 1.0.10 (2025-06-23), with main changes as follows:<br/>1. Add rv1126b support<br/>2. Update sys_cfg function to correct alignment issues across chips<br/>3. Add kmpp module; supports kmpp flow in mpi_enc_test<br/>4. Support hevc yuv444 10bit decoding on rk3576<br/>5. Support temporal_id configuration for encoded frames<br/>6. Separate forced decoding from error reporting<br/>7. Correct jpeg encoder hardware selection<br/>8. Fix vproc output frame ordering<br/>9. Add new kmpp_obj module support<br/>10. Correct yuv400 decoding support for rk1126b<br/>11. Correct gdr code stream decoding support<br/>12. Fix pthread_setwait-related issues<br/>13. Fix static library compilation issues<br/>14. Fix avs field decoding issues<br/>15. Fix h264 encoding dpb management memory leak<br/>16. Add new encoder configurations |
| RKADK Update                  | 1. Compatible with RV1126B<br/>2. RKADK Muxer adds support for external stream encapsulation<br/>3. Add API descriptions:<br/>(1) RKADK_STREAM_VideoReset<br/>(2) RKADK_RTSP_VideoReset<br/>(3) RKADK_RTMP_VideoReset |
| APP_CVR Update                | 1. Mainly adapts to LVGL8.4<br/>2. Adapts to RV1126B RKADK<br/>3. Adapts to RV1126B RGA interface |
| PREEMPT_RT, XENOMAI Update    | 1. Add Kernel 6.1.118<br/>2. Add rv1126b chip adaptation<br/>3. Optimize kernel5.10 latency<br/>4. Update real-time development documentation |
| DPDK Update                   | Add DWMAC1000 support                                        |
| RKWIFIBT, RKWIFIBT-APP Update | 1. Update Infineon driver to resolve compilation errors in individual modules<br/>2. Update wifibt-init script to enhance stability<br/>3. Update RTL8723DS/8821CS drivers to support Kernel 6.1<br/>4. Add AIC USB/SDIO/PCIE driver support<br/>5. Fix bcmdhd driver anomalies when RT real-time patch is enabled<br/>6. Update RK960 driver to enhance stability<br/>7. Move wifi configuration files in RKWIFIBT-APP to /userdata/<br/>8. Fix memory leak in RKWIFIBT-APP after enabling obex |
| Secure Update                 | 1. Support verify config ip function<br/>2. Support deriving HMAC key from OEM OTP KEY<br/>3. Integrate official security patches<br/>4. Support automatic file recovery after abnormal power loss<br/>5. Correct supported length of oem otp key2 |
| Gstreamer Update              | 1. Fix inability to stop in single-frame decoding mode<br/>2. Fix decoding freeze in specific scenarios<br/>3. Fix issue where setting keyframe requests generates multiple keyframes |
| libmali Update                | G31/G52 bifrost GPU upgraded from g24p0-7 to g24p0-9:<br/>1. gles: Fix uniform buffer<br/>2. vulkan: Fix replay buffer memory leak (testable with vkcube)<br/>3. Add purge wait environment variable to control memory usage output:<br/>export MALI_REPORT_MEM_USAGE=1<br/>export MALI_PURGE_WAIT_PERIOD_NS=100000000<br/>4. Add precision environment variable to enforce shader precision:<br/>export SHADER_FORCE_PRECISION=0x333 |
| linux-rga Update              | 1. Add support for RV1126B chip<br/>2. Support more CSC configuration combinations<br/>3. Fix compilation errors in some environments<br/>4. Supplement YUV 10bit format offset alignment restrictions<br/>5. Fix anomalies in BT.709-limit range color gamut operation on some chips (driver recommended to update to 1.3.9)<br/>6. Fix imsetColorSpace() inability to configure src1/pat channel color gamut |
| rk ethercat Update            | Adapt driver to Kernel version 6.1.118                       |
| ROCKIT Update                 | Updated rockit from V1.7.26 to V1.7.27. Main updates:<br/>1. Resolve GDC module compilation issues on unsupported chips<br/>2. Fix GPU cache flushing, memory leaks, and invalid pool issues<br/>3. Support VPSS path parsing, RKISP39 additional frame info, HRADWARE VPSS format conversion<br/>4. Fix VO low-latency layer shutdown, DRM rendering thread, and layer refresh link errors<br/>5. GDC adds EIS exception handling, user EIS support, and multi-instance error fixes<br/>6. Fix VPSS channel frame acquisition, VO interface call order, and VDEC mode changes<br/>7. Adjust VENC frame rate control; add PSkip flag and non-reference settings<br/>8. Update RK3588/3576 VDEC libraries; rename third-party CJSON APIs |
| RKAIQ Update                  | Update RKAIQ from v6.9.0 to v6.30.4:<br/>1. Support rv1126b<br/>2. Update FEC version<br/>3. Update smartIr version<br/>4. Fix several bugs |
| NPU Update                    | Update RKNN from V2.3.0 to V2.3.2:<br/>1. Support RV1126B platform<br/>2. Improve support for einsum norm operations<br/>3. Add automatic mixed precision function<br/>4. Enhance graph optimization capabilities |
| Algorithm Library Update      | 1. Optimize RK3506 lvgl scaling acceleration<br/>2. Update audio algorithm library and model parameters; support new features such as filter and EQDRC pipeline |
| Update U-boot, rkbin          | 1. Change RK3576 BL31 runtime address to 0x60000 to improve system reboot stability<br/>2. Add support for RK3582 chip |
| Update Kernel                 | 1. Kernel 6.1 upgraded to 6.1.118<br/>2. Add support for RV1126B chip |
| Update Tools                  | 1. RKDevTool upgraded from v3.36 to v3.37<br/>2. Update anti-board copying tool to V1.01<br/>3. Update DDR-related tools<br/>4. Update pin_debug_tool to v1.18<br/>5. Update programmer_image_tool to v1.28<br/>6. Update device writing tool to V1.3.7 |
| Update Documentation          | 1. Update Real-Time-Performance related patches for Kernel 6.1.118<br/>2. Update buildroot CSV/CVEs<br/>3. Complete Chinese and English documentation<br/>4. Update IP-related documentation for Linux, general, and other categories<br/>5. Update chip-related documents such as software development guides and Quickstart |

## rk3588_linux6.1_release_v1.2.0_20241220.xml Note

### Summary of Major Updates

- Added Buildroot LVGL9.1 support
- Added support for recovery ubifs
- Added RT patch support for  6.1.99
- Updated kernel: Kernel6.1 from 6.1.84 to 6.1.99,
- Updated NPU: RKNPU2 from V2.2 to V2.3
- Updated GPU: G31/G52/G610 DDK from 13p0 to g24p0 version
- Updated RKWIFIBT: Updated RKWIFIBT-APP from V1.6.1 to V1.6.2
- Updated Weston from Weston13 to 14.0.1
- Support for independently configuring recovery kernel parameters to achieve trimming of the recovery kernel
- Support for packaging linux-headers development packages to achieve Debian board-side kernel module compilation support
- Improved Debian SDK compilation environment checks and prompts under Ubuntu 24.04
- Support for compiling and packaging buildroot development environment SDK packages
- Optimization of yocto SDK configuration file-related processes
- Support for more file system formats under UBI for user partitions

### SDK Component Update Status

| **Module** | **Content** |
| :---------- | :--------------- |
| Security Upgrade |1. **Linux Kernel**: Security updates have been made to the Kernel6.1, upgrading from version 6.1.84 to 6.1.99, and for kernel5.10, from 5.10.209 to 5.10.226. For specific details, please refer to the official release [linux-cve-announce](https://lore.kernel.org/linux-cve-announce/). <br/>2. **Buildroot**: Upgraded to [Buildroot 2024.02](https://git.busybox.net/buildroot/plain/CHANGES?id=2024.02). <br/>3. **Yocto**: Security updates have been conducted, with the current version of Yocto5.0 being 5.0.3. You can find more information in the [release-notes-5.0.3](https://docs.yoctoproject.org/migration-guides/release-notes-5.0.3.html). The current version of Yocto4.0 is 4.0.17. You can refer to the [official documentation](https://docs.yoctoproject.org/migration-guides/release-notes-4.0.17.html). <br/>4. **Debian**: Debian11 has been updated to version 11.11 with security patches. Detailed information can be found in [Debian11](https://www.debian.org/News/2024/2024083102). Debian12 has been updated to version 12.8 with security patches. Similarly, detailed information can be found in [Debian12.8](https://www.debian.org/News/2024/20241109). |
| Update Buildroot | 1. Added support for lvgl9.1 and fixed issues with dependencies, animation types, DRM driver updates, and support for alpha channels.<br/> 2. Flutter updated to the latest version, with added support for drm-gbm and x11 rendering backends.<br/> 3. Weston upgraded to 14.0.1, fixing issues with weston cursor hiding, mirror mode, and performance regression.<br/>4. Added retroarch support and updates to some emulators.<br/>5. Added more partybox configurations and feature support.<br/>6. Added support for rk3506/3502 quick boot, secureboot, robot, and other features.<br/> 7. Added RK3576 MOS in-vehicle multi-system support.<br/> 8. Added gpu mesa3d support. |
| Update Debian | 1. Updated rkaiq to V6.9.0.<br/>2. Updated g31/g52/g610 from g13p0 to g24p0.<br/>3. Updated rknpu2 to v2.3.0.<br/>4. Fixed memory leak issue caused by input method wake-up from sleep.<br/>5. Updated mpp/gstreamer/rga and other hardware acceleration features to adapt.<br/>6. Added weston/wayland feature support. |
| Update Yocto | 1. Updated Yocto to 5.0.3 LTS.<br/>2. Upgraded chromium 129 130 131.<br/>3. Yocto SDK support for packaging wic firmware suitable for UFS storage.<br/>4. Fixed support for RK3399 DP function cabinet. |
| Update RTOS | 1. Optimized cmbacktrace code size, reducing memory usage.<br/>2. Fixed the size calculation issue of rt_hw_cpu_dcache_ops(), improving the accuracy of cache operations.<br/>3. Resolved compiler errors when Os is enabled, enhancing the stability of the compilation process.<br/>4. Supported SPI freeloop testing, enhancing hardware testing support.<br/>5. Updated tools to version v1.1.0, enhancing tool functionality.<br/>6. Added support for multiple virtual GPIO groups.<br/>7. Added support for Hym8653 RTC driver.<br/>8. Added support for led tube aip1629 driver. |
| Update RKWIFIBT, RKWIFIBT-APP | 1. Updated rtl8852be driver version.<br/>2. Updated ap6398s firmware.<br/>3. Fixed errors in wifibt-util.sh.<br/>4. Fixed bt music blockage issue in rk960.<br/>5. Improved wifi interface detection.<br/>6. Fixed errors in wifibt-init.sh when wlan0 is renamed.<br/>7. Supported RTL8852BU and fixed errors in parsing USB chip.<br/>8. Updated wifibt-app to version v1.6.2.<br/>- Supported Apple Notification Center Service (ANCS) specification.<br/>- Supported BLE read/write ATT_MTU report.<br/>- Fixed scan type error.<br/>- Supported managing BLE/BREDR with the same address.<br/>- Updated SPP API.<br/>- Supported reporting disconnection reasons to users.<br/>- Added Bluetooth configuration profiles (/data/main.conf: ssp/sc/gatt_client/discovery time/control mode).<br/>- Supported custom PIN codes for ssp_disable.<br/>- Supported debug information options.<br/>- Supported WPA2_WPA3 mixed encryption.<br/>- Supported pairing confirmation callback.<br/>- Fixed errors in bt_on/off test.<br/>- Refactored bt_test.c's bt_test_vendor_cb.<br/>- Refactored bt/ble name fields. |
| Update PREEMPT_RT, XENOMAI | 1. Added real-time patches for Kernel 6.1.99 and Kernel 5.10.226. |
| Update Secure | 1. Fixed rpmb key verification failure.<br/>2. Corrected RSA OAEP MGF1 algorithm.<br/>3. Corrected the condition for enabling/disabling secure boot. |
| Update rkscripts | 1. Supported more UBI file systems.<br/>2. Fixed device recognition issues when ADB coexists with other functions on Windows.<br/>3. Modified bootanim, log-guardian, and usbdevice to make logging functionality optional.<br/>4. Compatible with BusyBox's xargs.<br/>5. Fixed detection issues with ro/rw flags in fstab.<br/>6. Fixed NAND flash memory recognition by name.<br/>7. Fixed repeated partition errors. |
| Update Gstreamer | 1. Fixed random crashes caused by encoding during seek operations. |
| Update libmali | G31/G52 bifrost GPU from g13p0 to g24p0-7:<br/> 1. Support for EGL 1.5 version.<br/>2. X11 winsys default to enable xcb DRI3 interface specification, support setting environment variable MALI_X11_PREFER_DRI3=1/0 to switch between DRI2/DRI3 interface implementations.<br/>3. Support for SRGB color space EGLImage as a rendering target.<br/>4. Added interface extensions and window protocol support:<br/>OpenGL:<br/> - GL_EXT_clear_texture<br/> - GL_EXT_EGL_image_storage<br/> - GL_EXT_polygon_offset_clamp<br/> - GL_ARM_shader_core_properties<br/>GL_KHR_debug<br/>OpenCL:<br/> - cl_khr_command_buffer_mutable_dispatch<br/> - cl_ext_image_drm_format_modifier<br/> GBM:<br/> - GBM_BO_IMPORT_EGL_IMAGE<br/> - Wayland Protocol:<br/> - zwp_linux_explicit_synchronization_v1<br/>Support for third-party libwayland-egl library. |
| Update linux-rga | 1. Fixed compilation errors when printing int64_t.<br/>2. Removed bi-linear (downscaling) limitations.<br/>3. Checked the width and height of im_rect.<br/>4. Supported automatic configuration of RFBC mode.<br/>5. Supported automatic configuration of store_mode based on GraphicBuffer.<br/>6. Fixed definition errors for YUV_422_semi_planar format.<br/>7. Supported mixing between formats without per-pixel alpha. |
| Update rk ethercat | 1. Adapted driver updates to kernel version 6.1.99. |
| Update LVGL | 1. Supported DRM setting resolution.<br/>2. Fixed SDL compilation errors.<br/>3. Supported LVGL 9.1.<br/>4. Updated and optimized LVGL drivers.<br/>5. Updated rkaudio audio library.<br/>6. Removed redundant links.<br/>7. Fixed touch status checks. |
| Update RKADK | 1. Added VO display buffer length configuration.<br/>2. Adapted MPI screen resolution to RTT.<br/> 3. Fixed audio read thread deadlock when replaying + jumping.<br/>4. Adapted RK3576 platform. |
| Update ROCKIT | Updated rockit from V1.25 to v1.7.26. Main updates are as follows:<br/>1. Added support for RK3562 chip.<br/>2. Modified vdec buffer size and virtual width.<br/>3. Fixed issues in V4L2 module with different processing using the same address, illegal value use of local variables, and non hdmirx type calls to hdmi rx interface.<br/>4. Added function to get a single frame from isp.<br/>5. Renamed media - ctl functions to avoid naming conflicts.<br/>6. Fixed rkisp2.0 multi-sensor topology parsing, gdc compilation differences, glpss stack overflow, and mosaic layer information setting issues.<br/>7. AI AO module added VQE reload test.<br/>8. Fixed coredump issue with VO RGA composer when using RK_MPI_VO_DisableChn.<br/>9. SKV: Fixed coredump issue due to header file mismatch.<br/>10. RGA: Updated 64-bit C version and header files.<br/>11. Fixed VI binding VENC failure to get frames from HDMI RX node.<br/>12. Fixed encoding MPP crash issues, supporting additional multiple channels. |
| Update AUDIO | 1. Default enabled ES8388 sound card OUT1/OUT2 switches.<br/>2. Added initialization configuration for rk730.<br/>3. Added initialization configuration for alsa-utils and alsactl.<br/>4. Added support for es8388 sound card. |
| Update DPDK | 1. Added rtl8125 driver.<br/>2. Updated GMAC DPDK documentation.<br/>3. Optimized stmmac network driver.<br/>4. Reduced invalid cache operations. |
| Update RKIPC | 1. Fixed iva algorithm return value issue.<br/>2. Added default values for encoding-related advanced parameters.<br/>3. Fixed multi-view is/avs related issues. |
| Update RKAIQ | Updated RKAIQ version to v6.9.0: <br/>1. Matched isp driver v2.9.0.<br/>2. Tuning tool supports awb, ae api methods.<br/>3. Fixed some minor bugs.<br/>4. Added RK3588 EIS exposure information to isp driver. |
| Update NPU | Updated RKNN from V2.2.0 to V2.3.0 <br/>1. RKNN-Toolkit2 supports ARM64 architecture.<br/>2. RKNN-Toolkit-Lite2 supports installation via pip.<br/> 3. Added support for W4A16 symmetric quantization (suitable for RK3576).<br/>4. Optimized multiple operators, including: LayerNorm, LSTM, Transpose, MatMul, etc. |
| Update Algorithm Library | 1. Optimized VQE AI noise reduction algorithm effect, fixed exception handling process.<br/>2. Updated EQDRC version parameters, supporting current bin version recognition settings.<br/>3. Supported configurable continuous wake-up command words. |
| Update MPP | MPP updated to V1.0.8, main changes are as follows: <br/> 1. Added sys_cfg function, used for stride / fbc parameter consistency solutions between modules.<br/>2. Added jpeg decode support for put / get interfaces and decode interface.<br/>3. Added some modules supporting kmpp.<br/>4. Supported dictionary tree import/export function and callback function.<br/>5. Supported decoder hardware selection function.<br/>6. Supported vpuapi interface's disable_error function.<br/>7. Fixed encoder cpb parameter frame count calculation issue in long reference cases.<br/>8. Modified mpeg4 split flag judgment issue.<br/>9. Optimized encoder default tune module parameter configuration.<br/>10. Fixed some roi-related issues.<br/>11. Fixed some fast_play related issues. |
| Update Recovery | 1. Added ubifs support.<br/> 2. Fixed U disk firmware upgrade error issue. |
| Update U-boot, rkbin | 1. Improved RK3576/RK3588, RK356X DDR stability.<br/>2. RK3576J/M chip support patch.<br/>3. Solution for RK3576 OTP being probabilistically miswritten.<br/>4. Supported configuring sleep pin for sleep/wake.<br/>5. Supported resetting hptimer after sleep/wake.<br/>6. Optimized hptimer usage process.<br/>6. Added support for RK3576S. |
| Update Kernel | 1. Kernel6.1 upgraded to 6.1.99.<br/>2. Kernel5.10 upgraded to 5.10.226.<br/>3. pl330 dma driver chain list panic.<br/>4. RK3588 VOP aclk too low causing screen flashing and reporting POST_BUF_EMPTY issue.<br/> 5. The RK3588 enables the PCIe Active State Power Management (ASPM) L1SS function, which leads to abnormal WIFI firmware communication after the system resumes from sleep/wake. |
| Update Tools | 1. RKDevTool upgraded from v3.32 to v3.36.<br/> 2. pin_debug_tool upgraded from v1.16 to v1.17.<br/> 3. Updated upgrade_tool from v2.36 to v2.44.<br/> 4. Updated Linux_Pack_Firmware's rockdev. |
| Update Documentation | 1. Updated patches related to Real-Time-Performance for kernel 6.1.99 and 5.10.226.<br/>2. Updated buildroot csv.<br/>3. Complete Chinese and English documentation.<br/> 4. Imported new font for documentation.<br/> 5. Updated Linux, general, and other category IP-related documentation.<br/> 6. Updated software development guides, Quickstart, and other core documents. |

## rk3588_linux6.1_release_v1.1.1_20240920.xml Note

### Summary of Major Updates

- Increase support for setting screen resolution in virtual terminals
- Enhance compilation environment checks
- Optimize the adbd password verification mechanism
- Optimize the user partition configuration mechanism
- Support packaging kernel modules
- Fix Debian power button sleep and wake-up exceptions
- Fix exceptions in the linux-headers development package
- Fix exceptions in usbmount automatic mounting
- Fix compilation exceptions in Ubuntu 24.04

### SDK Component Update Status

| **Module** | **Content** |
| :---------- | :--------------- |
| Buildroot              | 1. Weston upgraded to 13.0.3<br/>2. Fixed individual VNC exceptions in Weston<br/>3. Support for fixing the Year 2038 problem<br/>4. Support for uvc-gadget<br/>5. Configuration of domestic download mirrors<br/>6. Fixed exceptions in non-desktop environments for Weston<br/>7. Added support for Mupen64Plus and RetroArch game emulators, along with configuration and performance optimizations<br/>8. Added RKADK backend support<br/>9. Added Kconfig to synchronize with the official LVGL source code, supporting the automatic generation of lv_conf.h configuration files<br/>10. Fixed opengles image tearing issues in certain cases for lv_drivers<br/>11. Fixed RGA exceptions within lv_drivers<br/>12. Introduced lvgl anti-initialization<br/>13. Added support for rockchip-uvc-app<br/>14. Updated alsa-utils to version 1.2.12 from the Buildroot upstream<br/>15. Updated valgrind to version 3.23.0 from the Buildroot upstream<br/>16. Default GCC updated from 12.3 to 12.4<br/>17. Updated dhcpcd to version 10.0.8 from the Buildroot upstream<br/>18. Updated Rockchip Valhall G610 to version g24p0<br/>19. Updated Chromium to 126.0.6478.126<br/>20. Updated usbmount, using flock instead of lockfile to improve multi-partition mounting speed, ignoring persistent storage such as UFS, adding a fallback mechanism for automatic file system type detection (in case blkid reports incorrectly), and improving recognition of devices using the ATA bus (e.g., sd*)<br/> |
| Debian | 1. Updated the package-patches directory for third-party custom packages<br/>2. Added support for weston/wayland hardware acceleration<br/>3. Updated rkaiq/rknpu2/mpp/gst-rkmpp/rga2/libmali libraries to adapt to the new version of the SDK<br/>4. Upgraded the Chromium browser to the LTS version 126.0.6478.126<br/>5. Added ibus Chinese input method support<br/>6. Added the light-locker package to resolve the lock screen function ineffectiveness issue<br/>7. Added the eject package to resolve the automatic ejection function for some devices |
| Yocto | 1. Updated Yocto to 5.0.3 LTS<br/>2. Upgraded chromium to versions 124, 125, 126<br/>3. Supported Gstreamer 1.22.12 |
| RTOS | 1. Added flexbus, DAC mode, ADC mode, BSP support, and updates to the HAL core library<br/>2. Enhanced USB functionality, including adding phy id parameters, increasing core soft reset time, etc.<br/>3. Updated the ota module to support the new OTA upgrade process<br/>4. Added support for multiple audio devices and drivers |
| RKWIFIBT, RKWIFIBT-APP | 1. Improved the power consumption of audio communication through I2S/PCM during calls, reduced call latency, and enhanced the experience<br/>2. Improved Bluetooth compatibility with Windows 7/10/11<br/>3. Improved the functionality of call AT commands, such as answer/hang up/redial, solving the issue of some Windows systems not sending AT commands<br/>4. Improved the phone book function to fully obtain: complete contacts/call records/missed records, etc.<br/>5. Added a mix description to facilitate customers' management of multi-channel audio<br/>6. Added file transfer functionality and API, enabling bidirectional file transfer with mobile phones and PCs<br/>7. Newly added support for iOS system ANCS notification functionality, similar to smartwatch notification functionality<br/>8. Newly added support for 6.10 kernel Infineon module drivers: including some traditional driver upgrades and new module WiFi6/6E support |
| PREEMPT_RT, XENOMAI | 1. Ported the real-time patch of kernel 6.1.84<br/>2. Documentation updated |
| Optee | 1. Added support for optee's ufs rpmb<br/>2. Updated rk_tee_user<br/>3. Support for reading and writing Non-Protected OEM Zone area OTP data<br/>4. Support for software TA encryption key functionality, allowing customers to use TA encryption functionality without burning keys<br/>5. Support for block reading of RPMB data<br/>6. Disabled Keylad's OTP zero bit count function<br/>7. Support for OTP hardware lock functionality, allowing secure and non-secure OTP to access simultaneously |
| rkscripts | The update of the rkscript repository mainly focuses on the improvement of USB device configuration, including support for custom PID, reducing warnings, fixing typos, prioritizing the ntfs3 driver, UMS fallback mechanism, forcing local loopback, cleaning up old files during initialization, running file system checks when configuring UMS, retrying when starting fails, and adding example hook functions for rndis |
| Gstreamer | 1. Fixed occasional stuttering for some video sources<br/>2. Fixed frame skipping for some de-interlaced video sources |
| libmali | 1. Updated G31/G52/G610 to G13p0-11:<br/>- Fixed the low probability of crash when the dummy backend calls eglChooseConfigs<br/>- Supported SRGB color space FBO as a rendering target<br/>- Mali-G52 GPU added support for wayland-dummy-gbm backend<br/>2. G610 userspace driver upgraded from g13p0-10 to g24p0-3, main updates include<br/>- Supported EGL 1.5 version<br/>- Fixed issues with ARB/EXT_robustness extension interface support in g13p0 version |
| linux-rga | Fixed and improved the functionality of im2d_api, such as format checking, fence processing, and blending support |
|rk ethercat | 1. Adapted the driver program update to kernel version 6.1.84.<br/>2. Optimized the reception of data packets after sending them, which is better than receiving them after nanosleep. |
| lvgl | 1. Adapted to the RKADK backend<br/>2. Added ASR functionality<br/>3. Added sensor detection capabilities<br/>4. Added backlight control<br/>5. Added bubble prompt controls<br/>6. Adjusted the startup logic and settings interface for WiFi and BT<br/>7. Adjusted and fixed some UI interaction logic exceptions. |
| RKADK | 1. Added Picture-In-Picture (PiP) recording functionality<br/>2. Added support for JPEG FBC0/NV16 encoding<br/>3. Added API documentation:<br/>   (1) RKADK_RECORD_Single_Start<br/>   (2) RKADK_RECORD_Single_Stop<br/>   (3) RKADK_RECORD_SetPipAttr<br/>   (4) RKADK_RECORD_FileCacheSetMode<br/>   (5) RKADK_PLAYER_GetSendFrameNum<br/>   (6) RKADK_PLAYER_SetVdecWaterline<br/>   (7) RKADK_PLAYER_SetAoVolume |
| ROCKIT | Updated rockit from version V1.22 to v1.7.25. The main updates are as follows:<br/><br/>AUDIO:<br/>1. Expanded the number of audio channels.<br/>2. Removed JSON parsing from VQE.<br/>3. Updated SFS and EQ parameters to support AI-NR.<br/>4. Added support for parsing EQ features.<br/>5. Added support for parsing AGC of AO (RX) VQE.<br/>6. Added an option to use MONOTONIC for PCM when BOOTTIME fails.<br/><br/>VI:<br/>1. Prevented repeated initialization of the V4L2 device.<br/>2. Implemented post-processing for VI.<br/>3. Fixed frame rate issues with HDMI RX interlaced scanning.<br/>4. Fixed exceptions with HDMI RX YUV422 non-64-byte alignment.<br/>5. Added an API to enable single-frame capture.<br/><br/>VO:<br/>1. Added documentation for RK3576.<br/>2. Removed the dependency of the VO module on the GPU for initializing the Weston desktop.<br/><br/>VENC:<br/>1. Supported resolution changes in VENC.<br/>2. Updated the RC parameters for VENC.<br/><br/>VPSS:<br/>1. Configured the hardware VPSS sequence.<br/>2. Implemented adaptation to the hardware ISP.<br/>3. Updated VPSS documentation to version v1.1.5. |
| AUDIO | 1. Enabled the OUT1/OUT2 switch of the ES8388 sound card by default<br/>2. Added initialization configuration for rk730<br/>3. Added initialization configuration for alsa-utils and alsactl<br/>4. Added support for the ES8388 sound card. |
|RKIPC | 1. ISP white balance/contrast/hdr/frame rate issues<br/>2. VO compatibility with HDMI and MIPI displays, and fixed deinitialization issues<br/>3. Corrected OSD color and frame problems<br/>4. Updated AVS stitching parameters<br/>5. Adapted to rkaiq version 6.8.0, using functional-level APIs for all, fixing dozens of related issues, and improving stability<br/>6. Added rockiva face and human body recognition frame functions<br/>7. Supported HDMI and MIPI displays<br/>8. Optimized OSD-related logic<br/>9. Supported AIISP functionality |
| RKAIQ | Updated RKAIQ version to v6.8.0:<br/>1. Supported ldc/ldch<br/>2. Solved mirror/flip, wb, and other imgproc interface issues<br/>3. AIQ default direct pass-through mode, rk_aiq_uapi2_sysctl_setMulCamConc interface 1103b failure<br/>4. Fixed 4k ae, awb exceptions<br/>5. Updated AF IQ parameters affecting old platforms such as 1106, 3588, etc., cpp versions<br/>6. Solved the reddish bias problem caused by quick start blc<br/>7. Solved some bugs in group mode<br/>8. IQ deleted YME, CPSL<br/>9. Solved cac, ldch memory leaks<br/>10. Updated IQ structure: btnr, hsv, histeq, enh<br/>11. Imgproc: Fixed the issue of not restoring the setting of btnr when preparing to set the mirror/flip<br/>12. Fixed the ae flicker problem of isp3x/isp21 caused by blc since v5.1.3<br/>13. AeHandler: Set the ISO value to the shared information when aiq is prepared<br/>14. Solved the problem of settings like dehaze not taking effect in the 3576 surround view mode<br/>15. RK3576 supports dumpsys, an additional 30kb |
| NPU | Updated RKNN from V2.0.0-beta01 to V2.2.0<br/>1. Supported RK1103B<br/>2. Supported RK2118<br/>3. Supported Flash Attention (Only RK3562 and RK3576), optimized transformer model performance<br/>4. Optimized support for int32 and int64 data types<br/>5. Supported more operator fusion<br/>6. Operator optimizations, such as softmax, hardmax, MatMul, etc.<br/>7. Supported RK3576 W4A16 symmetric quantization<br/>8. Supported installation via PYPI<br/>9. Supported Python 3.12<br/>10. rknn_model zoo supports demos like mobilesam, whisper Chinese, zero copy, etc. |
| MPP | MPP updated to V1.0.7, with the following main changes:<br/>1. Merged encoder tuning branch code<br/>2. Optimized MppTrie structure<br/>3. Supported H.265's mlvec LTR related functions<br/>4. Supported H.264's hdr information parsing<br/>5. Fixed the stream abnormality issue with tsvc short delay output in CAVLC cases<br/>6. Fixed the exception when two consecutive sps occur during info change<br/>7. Fixed the maximum mv length marking issue in H.264 sps<br/>8. Fixed GDR related issues<br/>9. Fixed issues related to low-latency output<br/>10. Fixed some memory leak issues<br/>11. Fixed some decoding issues with av1, H.265, and mpeg2 |
| U-boot, rkbin |  1. Updated RK3576 DDR binary to V1.07, resolving the instability of LPDDR4X 2112MHz on a few boards due to unreasonable rx dqs vref configuration<br/>2. Updated RK356X DDR binary to V1.23, mainly solving the following issues:<br/> a. Added read/write Vref training to improve DDR signal compatibility.<br/> b. Enabled rx odt at LPDDR4/4x 780MHz to improve stability.<br/> c. Solved compatibility issues with some LP4x 324M.<br/> d. Resolved potential capacity detection anomalies or ECC activation bugs for DDR4.<br/>3. Updated the RK3326/PX30/RK3358 DDR binary to V2.11, addressing the issue of DDR4 capacity detection missing by half or a quarter for PX30/RK3326/RK3358.<br/>4. Resolved the failure to enter the U-Boot Loader using the Linux-6.1 kernel on the RK3568 platform.<br/>5. Supported SPI Nand CONT_READ.<br/>6. Added SPI Nor Auto_Merge code to facilitate the convenient operation of applying 2 on-chip SPI Nor flash memories to 1 device.<br/>7. Modified the erase protection function to allow vendor storage data to be erased.<br/>8. Modified MPHY power supply judgment to resolve some UFS support anomalies.<br/>9. Added controller CRU reset to resolve some UFS initialization anomalies. |
| Kernel 6.1 | 1. Resolved the WIFI FW communication anomaly after enabling ASPM L1SS on RK3588 PCIe and resuming from hibernation.<br/>2. Added the function for rk3588 to enable optee to respond to Linux kernel interrupts.<br/>3. Resolved the silent playback issue when switching from 48k sampling rate to 16K/8K on RK809·RK817-(A version) for the first time.<br/>4. [I2STDM] Resolved the low-probability 1-bit shift issue in the RX under TRCM-TX scenario.<br/>5. Resolved the issue of multi-channel audio switching not working and recording anomalies on RK3568 Debian.<br/>6. Resolved the issue of RK3568 SATA not being recognized.<br/>7. Resolved the RK3566 Bluetooth failure anomaly.<br/>8. Resolved the page fault issue when iep2 is in I1O1T mode on some resolutions. |
| Tools | 1. RKDevTool upgraded from v3.31 to v3.32.<br/>2. pin_debug_tool upgraded from v1.13 to v1.16.<br/>3. Updated RKDevInfoWriteTool.<br/>4. Updated RKDevTool rockdev. |
| Documentation | 1. Updated patches related to Real-Time-Performance for kernel 6.1.84.<br/>2. Updated buildroot csv.<br/>3. Imported more customer-demanded development documents such as DMSC\FLEXBUS.<br/>4. Updated the support list for eMMC/DDR/Nand.<br/>5. Added RTT-related documentation.<br/>6. Updated IP-related documents for Linux, general, and other categories.<br/>7. Updated the software development guide, adding support for RK3576 and more features. |

## rk3588_linux6.1_release_v1.1.0_20240620.xml Note

The new features and functionalities of the SDK, along with a comprehensive set of updates, span across a wide array of areas including tool and script updates, configuration file improvements, specific chip support, kernel and system build enhancements, system optimizations, security and permissions updates, support for specific hardware or features, bug fixes, and documentation and example updates. The goal of these updates is to enhance capabilities, fix bugs, improve user experience and system performance, and ensure better security and compatibility.

### Summary of Major Updates

- Tool and Script Updates: Enhanced functionalities, bug fixes, and improved user experiences.
- Configuration File Improvements: Optimized help information and default configurations.
- Chip-Specific Changes: Updates and improvements to configurations for chips like rk3308, rk3588, and rk3562.
- Kernel and System Build: Build script improvements to avoid warnings and fix compilation errors.
- Tool Additions: Addition of new tools such as inotify-tools, adb support, etc.
- System Optimizations: Improvements in system startup, logging, storage checks, etc.
- Security and Permissions: Updates to security scripts and configurations, enhanced kernel security.
- Support for Specific Features: Added support for specific hardware or features like amp_mcu, rk3576 multi-camera support, etc.
- Bug Fixes: Fixed compilation errors, type errors, warning messages, etc.
- Documentation and Example Updates: Updated README files and example codes to reflect the latest changes and features.

### Updates to SDK Components

- Security Upgrades: Security updates for Linux Kernel, Buildroot, Yocto, Debian, etc.
- Buildroot Updates: Fixes for ncurses library, configuration updates for lvgl and lvgl_demo, added support for packages, etc.
- Debian Updates: Solved issues with the Cheese application, updates to mpp/libv4l/gst-rkmpp/rga2 libraries, etc.
- Yocto Updates: Updates to Yocto 5.0 LTS, upgrades to the v4l-rkmpp package, etc.
- RTOS Updates: Multiple updates to Rockchip BSP, including support for platforms like rk3588-64 etc.
- RKWIFIBT Updates: Added compatibility with more wireless network hardware, updates to applications and drivers.
- Updates to PREEMPT_RT, XENOMAI: Real-time patch porting, documentation updates.
- RKSCRIPTS Updates: Fixed UVC errors, updated product ID lists.
- Updates to Xserver, Gstreamer, libmali, liux-rga, IVA, LVGL, RKADK, ROCKIT, RKUPDATE, AUDIO, RKIPC, RKAIQ, NPU, DPDK, MPP, Kernel6.1: Extensive updates including feature additions, performance improvements, bug fixes, etc.
- ROCKCHIP-TEST: Updated reboot test scripts, added support for rknn_demo.
- Tool Updates: Upgraded various tools such as rk_ddrbin_tool, upgrade_tool, etc., and added new tools.
- Documentation Updates: Updated a large number of development documents, including real-time performance, licenses, customer requirements, kernel support, etc.

## rk3588_linux6.1_release_v1.0.0_20231220.xml Note

```
- The first release version
```
