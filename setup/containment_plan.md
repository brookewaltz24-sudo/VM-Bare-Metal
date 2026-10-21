## Sample Handling

- Samples are sourced only from MalwareBazaar, with known SHA-256
  hashes logged alongside results.
- Samples are kept in a password-protected archive, encrypted at rest,
  until the moment of use.
- A dedicated, write-protected USB (hardware write-blocker) is used
  only for sample transfer — never for logs, images, or anything else.
- Each sample's hash is re-verified immediately before every run, not
  only when first logged.
- Samples tagged VM-aware/evasive are checked with capa to confirm
  anti-VM capability in the code itself, rather than trusting the tag.

## Log Handling

- At the end of each bare-metal run, the machine is shut down and
  booted from a Linux live USB. The Windows disk is mounted read-only,
  and only text-based logs (CSV, TXT, PCAP) are copied to a dedicated,
  single-purpose log-out USB.
- Logs are never opened on the infected install or on the main host
  directly. On the VM side, logs are exported from within the guest
  before reverting the snapshot.
- Logs are treated as untrusted, since a sample may tamper with or
  delete its own traces. This is a documented limitation of the
  bare-metal data specifically.

## Known Limitations

- Firmware-level integrity is not directly verified after each run
  (full attestation tools like CHIPSEC were out of scope for this
  timeline). A verified BIOS recovery image is the mitigation in place.
- Some monitoring tool artifacts (Regshot's compiled-in window title,
  FakeNet-NG's listening behavior) cannot be fully hidden without
  rebuilding from source and are documented rather than eliminated.
