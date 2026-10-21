- Hardware: Dell OptiPlex 7010. No Wi-Fi or Bluetooth hardware is
  present, so there is no wireless path to disable.
- PXE/network boot and Wake-on-LAN are disabled in BIOS.
- The CPU (i5-3470) is confirmed non-vPro, so there is no Intel AMT
  out-of-band management to worry about on this hardware.
- The machine is never connected to any real network. FakeNet-NG
  (single-host mode) simulates network connectivity so samples believe
  they have internet access.
- The machine is re-imaged from a checksum-verified Clonezilla image
  after every single sample run, regardless of whether the environment
  looks clean. Restored partitions are hash-verified against the
  recorded baseline before the system is ever booted.
- The Clonezilla image drive and boot USB are physically unplugged
  during every sample run, not just left idle, since wipers/ransomware
  can target any attached disk.
- A separate, verified BIOS recovery USB (`BIOS_IMG.rcv`) is kept on
  hand in case of suspected firmware tampering.
