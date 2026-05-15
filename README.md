# Custom High-Performance PC Build — Documentation & Troubleshooting Log

A full end-to-end documentation of planning, assembling, and configuring a custom desktop PC from scratch — including component research, hardware installation, OS setup, and real troubleshooting cases resolved during the build process.

---

## Build Specifications

| Component | Part |
|---|---|
| **CPU** | Intel Core i7-14700K |
| **Motherboard** | MSI PRO Z790-A MAX WiFi (LGA1700, DDR5, PCIe 5.0) |
| **RAM** | G.Skill Ripjaws S5 32GB (2x16GB) DDR5 6000MHz CL30 |
| **GPU** | MSI Gaming GeForce RTX 3060 12GB GDDR6 |
| **Storage** | Samsung 990 Pro 2TB NVMe M.2 PCIe Gen4 SSD |
| **Case** | Montech AIR 903 MAX E-ATX Mid Tower (Tempered Glass) |
| **PSU** | Corsair RM850e 850W Fully Modular 80+ Gold |
| **CPU Cooler** | Phanteks Phantom Spirit 120SE (Dual Fan Tower) |
| **Thermal Paste** | Arctic MX-6 High Performance |
| **Monitor** | Acer Nitro Series |
| **OS** | Windows 11 (clean install via bootable USB) |

---

## Why I Built Instead of Buying

Pre-built PCs at this spec level cost significantly more and often use lower-quality PSUs and cooling solutions. Building from scratch allowed full component control, better value, and hands-on understanding of every system layer — from BIOS configuration to driver management.

---

## Build Process

### 1. Component Research & Compatibility Verification
Before purchasing, verified full compatibility across:
- CPU socket: LGA1700 matches Z790 motherboard
- RAM type: DDR5 required for Z790 platform, selected 6000MHz for optimal performance on Intel 14th gen
- PCIe slot compatibility: RTX 3060 in PCIe x16 slot (Gen4)
- PSU wattage calculation: confirmed 850W sufficient for full system load with headroom
- Case clearance: confirmed E-ATX motherboard fits Montech AIR 903 MAX, CPU cooler height clearance checked

**Challenge:** First time building, the sheer number of connectors, slots, and cables was overwhelming. Resolved by cross-referencing the motherboard manual with YouTube build guides for the same platform before touching any hardware.

---

### 2. Hardware Assembly
- Installed CPU into LGA1700 socket — aligned correctly using the triangle marker
- Seated DDR5 RAM in correct slots per motherboard manual (A2/B2 for dual channel)
- Mounted NVMe SSD into M.2 slot (M.2_1, PCIe Gen4)
- Applied Arctic MX-6 thermal paste using pea-dot method on CPU IHS
- Mounted Phanteks cooler and routed fan headers to motherboard
- Installed RTX 3060 into PCIe x16 slot, secured bracket
- Connected all case cables (front panel, USB headers, audio)
- Routed PSU cables through case for clean airflow

---

### 3. OS Installation
- Downloaded Windows 11 ISO from official Microsoft website
- Created bootable USB using Rufus (GPT partition scheme, UEFI mode)
- Configured BIOS boot order to prioritise USB
- Performed clean installation — selected custom install, formatted drive, completed OOBE setup
- Activated Windows post-install

---

## Troubleshooting Log

### Issue 1 — No display output on first boot
**Symptom:** PC powered on (fans spinning, RGB active) but monitor showed no signal.

**Diagnosis steps:**
1. Checked all power connections — appeared correct
2. Reseated RAM — no change
3. Checked monitor input source — set to correct port
4. Examined cable routing — discovered monitor DisplayPort cable was connected to the **motherboard's integrated display output**, not the GPU

**Root cause:** RTX 3060 was fully seated but monitor was plugged into the motherboard's HDMI port. When a dedicated GPU is present, the iGPU output is disabled by default in BIOS.

**Fix:** Moved DisplayPort cable from motherboard output to RTX 3060's display output. System posted immediately.

**Lesson learned:** Always connect display to the GPU, not the motherboard, when a dedicated graphics card is installed. This is one of the most common first-build mistakes and an important reminder for any IT support scenario involving display troubleshooting.

---

### Issue 2 — GPU drivers not installing correctly
**Symptom:** After Windows 11 install, screen resolution was stuck at 1024x768 and GPU was showing as "Microsoft Basic Display Adapter" in Device Manager.

**Diagnosis steps:**
1. Opened Device Manager — confirmed no NVIDIA driver present
2. Attempted Windows Update — did not install correct GPU driver automatically
3. Went to NVIDIA website — downloaded GeForce Game Ready Driver manually

**Root cause:** Windows 11 did not automatically fetch the correct driver for the RTX 3060 post-install.

**Fix:** Downloaded and ran NVIDIA GeForce Game Ready Driver installer manually. Performed clean install option to remove any partial driver files. Rebooted — GPU recognised correctly, resolution restored.

**Lesson learned:** After a clean OS install, always manually install GPU, chipset, and network drivers from manufacturer websites rather than relying solely on Windows Update.

---

### Issue 3 — RAM not running at advertised 6000MHz
**Symptom:** System running but CPU-Z showed RAM running at 4800MHz instead of purchased 6000MHz speed.

**Diagnosis steps:**
1. Confirmed RAM installed in correct dual-channel slots (A2/B2)
2. Entered BIOS — found XMP/EXPO profile not enabled by default

**Root cause:** BIOS ships with XMP disabled. DDR5 high-speed profiles must be manually enabled.

**Fix:** Enabled XMP Profile 1 in BIOS (MSI calls it A-XMP). Saved and rebooted. RAM confirmed running at 6000MHz CL30.

**Lesson learned:** High-speed RAM never runs at advertised speeds out of the box — XMP/EXPO must always be manually enabled in BIOS.

---

## Skills Demonstrated

- Hardware compatibility research and component selection
- Full PC assembly including CPU, cooler, RAM, GPU, NVMe, PSU routing
- BIOS configuration — boot order, XMP memory profiles, display output settings
- OS deployment via bootable USB (Windows 11, GPT/UEFI)
- Driver installation and device management
- Systematic troubleshooting methodology — symptom → diagnosis → root cause → fix → lesson

---

## Tools & References Used
- Rufus (bootable USB creation)
- MSI BIOS (Z790 platform)
- NVIDIA GeForce Driver installer
- Windows Device Manager
- CPU-Z (system verification)
- PC Part Picker (compatibility check)

---

*This build is used as a home lab environment for hands-on IT support practice including virtualisation (VirtualBox), networking labs, Active Directory setup, and scripting projects and also beacuse i love playing video games*
