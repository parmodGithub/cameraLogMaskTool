What the tool does
 
A self-contained, single-file HTML tool that generates ADB commands for Qualcomm Spectra camera logging. It covers all three logging domains from the debug guide.:
 
Three tabs:
 
1. UMD Log Groups (sourced from `src/utils/camxtypes.h`)
- 40 groups: `CamxLogGroupAFD` (bit 0) through `CamxLogGroupPerf` (bit 38)
- Generates `logConfigMask`, `logInfoMask`, `logVerboseMask`, `logEntryExitMask`, `logWarningMask` commands for `/vendor/etc/camera/camxoverridesettings.txt`
 
2. KMD Log Groups
- 28 groups: `CAM_CDM` (bit 0) through `CAM_OPE` (bit 28)
- Generates `debug_mdl` command for `/sys/module/cam_debug_util/parameters/debug_mdl`
 
3. CSID Debug Groups 
- 8 groups: `CSID_DEBUG_ENABLE_SOF_IRQ` (bit 0) through `CSID_DEBUG_ENABLE_HBI_VBI_INFO` (bit 7)
- Generates `ife_csid_debug` command for `/sys/kernel/debug/camera_ife/ife_csid_debug`
 
Features:
✅ Checkbox selection for each module group
✅ Select all / Unselect all buttons
✅ Manual mask input — enter a hex mask (e.g. `0x10080`) to pre-select the corresponding groups
✅ Live mask computation — computed hex mask and decimal value update instantly
✅ ADB commands generated dynamically with the computed mask value
✅ Copy to clipboard button for each command block
✅ Syntax-highlighted command display (dark terminal style)
✅ Uses JavaScript `BigInt` to correctly handle 64-bit UMD masks
✅ No external dependencies — works fully offline as a single distributable HTML file
 