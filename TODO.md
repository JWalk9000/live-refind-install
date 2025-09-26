# rEFInd Installation Script - TODO & Features

## **Current Status**
- ✅ Basic rEFInd installation (chroot + live environment)
- ✅ Driver management system
- ✅ Basic Btrfs subvolume detection
- ✅ Basic LVM detection
- ✅ Architecture detection (x86_64, aarch64)
- ✅ ESP filesystem validation

## **Priority Features I'd like to Add**

### **High Priority**
- [ ] **Enhanced Btrfs Support**
  - [ ] Multi-device Btrfs detection
  - [ ] Btrfs RAID detection (RAID0, RAID1, RAID10, etc.)
  - [ ] Nested subvolume handling (`@home` inside `@`)
  - [ ] Btrfs compression detection (zstd, lzo, zlib)
  - [ ] Snapshot-aware boot entries
  - [ ] Multiple subvolume boot options

- [ ] **LUKS/dm-crypt Support**
  - [ ] Detect encrypted root partition
  - [ ] Generate `cryptdevice=UUID=...:cryptroot` parameters
  - [ ] Handle LUKS on LVM vs LVM on LUKS
  - [ ] Multiple encrypted device support
  - [ ] Key file detection

- [ ] **Enhanced ZFS Support**
  - [ ] ZFS dataset detection (`zroot/ROOT/default`)
  - [ ] Boot environment detection
  - [ ] Multiple bootable datasets
  - [ ] ZFS pool properties detection
  - [ ] `zfs=` parameter generation

### **Medium Priority**
- [ ] **Enhanced LVM Support**
  - [ ] LVM snapshot detection
  - [ ] Thin provisioning detection
  - [ ] Multiple volume group handling
  - [ ] LV path vs mapper path handling

- [ ] **RAID Support**
  - [ ] mdadm software RAID detection
  - [ ] Btrfs built-in RAID detection
  - [ ] Hardware RAID transparency check
  - [ ] RAID degraded state handling

- [ ] **Advanced Filesystem Support**
  - [ ] Bcachefs support (emerging)
  - [ ] F2FS with compression options
  - [ ] XFS with special mount options
  - [ ] Advanced ext4 features (encryption, etc.)

### **Low Priority / Nice to Have**
- [ ] **Configuration Management**
  - [ ] Custom refind.conf generation
  - [ ] Theme support and installation
  - [ ] Icon customization
  - [ ] Resolution and timeout settings
  - [ ] Boot menu customization

- [ ] **Advanced Features**
  - [ ] Secure Boot support
  - [ ] Multiple ESP handling
  - [ ] Network boot options (PXE, etc.)
  - [ ] Recovery mode entries
  - [ ] Memtest86+ integration

- [ ] **Error Handling & Recovery**
  - [ ] Backup existing bootloader
  - [ ] Rollback functionality
  - [ ] Boot repair mode
  - [ ] Validation and health checks

## **Known Issues / Improvements**

### **Current Limitations**
- [ ] No validation of kernel/initramfs existence before boot entry creation
- [ ] Limited error recovery if EFI registration fails
- [ ] No check for sufficient ESP space
- [ ] No handling of custom kernel names (e.g., custom compiled kernels)

### **Code Quality**
- [ ] Add comprehensive error handling for edge cases
- [ ] Improve logging and debug output
- [ ] Add unit tests for critical functions
- [ ] Better argument validation
- [ ] Configuration file support

### **Documentation**
- [ ] Complete README with examples
- [ ] Troubleshooting guide
- [ ] Architecture documentation
- [ ] Video/screenshot demonstrations

## **Future Considerations**

### **Emerging Technologies**
- [ ] Systemd-boot integration/comparison
- [ ] UEFI stub kernel support
- [ ] Container/immutable system support (Fedora Silverblue, etc.)
- [ ] Unified kernel images (UKI)

### **Multi-distro Support**
- [ ] Debian/Ubuntu support
- [ ] Fedora/RHEL support
- [ ] openSUSE support
- [ ] Gentoo support

### **Advanced Security**
- [ ] TPM integration
- [ ] Measured boot support
- [ ] Attestation and verification
- [ ] Key management

## **Implementation Notes**

### **Btrfs Priority Items** (Current Focus)
1. **Multi-device detection** - Handle Btrfs across multiple drives
2. **RAID level detection** - Detect and handle Btrfs RAID configurations
3. **Compression detection** - Add mount options for compression
4. **Snapshot boot entries** - Allow booting from Btrfs snapshots

### **Technical Debt**
- Refactor filesystem detection into modular functions
- Create a plugin architecture for filesystem-specific handling
- Separate configuration generation from detection logic
- Improve test coverage and validation

---

**Last Updated:** September 26, 2025
**Maintainer:** JWalk9000