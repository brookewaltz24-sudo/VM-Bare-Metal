- The Windows 10 guest and CAPE (Ubuntu Server) run as sibling VMs under
  VMware Workstation, with CAPE controlling the guest over the virtual
  network rather than through nested virtualization.
- The virtual LAN uses a host-only/custom VMnet only — no bridged or NAT
  adapter is present during analysis. NAT is used only during setup (e.g.
  downloading tools) and switched back before any sample is introduced.
- Shared folders, clipboard, and drag-and-drop are disabled on the guest
  once setup is complete, closing the only soft path back to the host.
- The host laptop's own network (Wi-Fi/Ethernet) is disconnected during
  sample runs as an additional safeguard.
- tcpdump runs on the CAPE VM during every containment test and sample
  run, confirming no traffic leaves the internal VMnet. A verified
  baseline test (`ping 8.8.8.8` from the guest) returns "Transmit
  failed" — no route exists out of the isolated network.
- A clean, hardened snapshot of the guest is restored before every
  sample run.
