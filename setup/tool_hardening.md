# Tool Hardening

Monitoring tools can themselves be detected by evasive malware, which
would compromise the comparison (a sample reacting to Procmon rather
than to the environment). This document records what was done to
reduce each tool's visibility, on both the VM guest and the OptiPlex,
and what limitations remain.

## General approach

- All tools (Procmon, Regshot, Autorunsc, FakeNet-NG) are portable
  executables — no installer, so none create Windows "Uninstall"
  registry entries. Nothing to clean up there.
- All tools are installed in one non-default folder (not Desktop,
  Downloads, or anything named "tools"/"analysis"), not inside
  C:\Windows\System32.
- Windows Defender exclusions are set for that folder on both machines
  so tools aren't quarantined mid-run.
- The same hardening is applied identically on the VM guest and the
  OptiPlex, so any residual detectability is symmetric and doesn't
  bias the comparison.

## Procmon

- Renamed executable (e.g. `Procmon64.exe` -> `svchelper.exe`).
- Installed with a custom driver name instead of the default:
  `svchelper.exe /AcceptEula /DriverName customdrv`
- Run minimized with background capture to a file, not the live GUI:
  `svchelper.exe /AcceptEula /Quiet /Minimized /BackingFile C:\logs\run.pml`
- Verified capture is active by checking the backing file grows in
  size during a test run, not just that the process is running.

## Regshot

- Renamed executable (e.g. `Regshot-x64-Unicode.exe` -> `sysutil.exe`).
- Installed/run from the same non-default folder as the other tools.
- **Limitation:** the window title is compiled into the binary and
  cannot be renamed without rebuilding from source. This was judged
  not worth the effort given the project timeline, and is documented
  here as a known, unresolved detection vector.

## Autoruns / Autorunsc

- Renamed executable (e.g. `Autorunsc64.exe` -> `sysreport.exe`).
- Run via the CLI version only (no GUI window):
  `sysreport.exe -accepteula -a * -c > C:\logs\autoruns_output.csv`

## FakeNet-NG

- Renamed executable.
- Run from the command line, not the GUI listener view.
- **Limitation:** its core function (opening broad listening ports,
  responding to arbitrary DNS/HTTP requests) is itself a detectable
  behavior pattern, independent of the filename. This cannot be
  hidden without changing how FakeNet-NG fundamentally works, and is
  documented as an inherent limitation rather than something fixed.

## VM-specific hardening (`.vmx` edits)

Applied to close detection vectors Pafish/al-khaser flagged that are
specific to running under VMware, separate from the tool-hiding work
above:

- `hypervisor.cpuid.v0 = "FALSE"` — hides the hypervisor bit and
  vendor string in CPUID.
- `smbios.reflecthost = "TRUE"` — pulls BIOS/serial/manufacturer
  strings from the host laptop's real hardware instead of VMware's
  defaults.
- Custom static MAC address (`ethernet0.addressType = "static"`),
  avoiding VMware's known OUI prefixes (00:05:69, 00:0C:29, 00:1C:14,
  00:50:56).
- Confirmed the guest still boots correctly after each change before
  moving to the next.

**Not fixed, documented as limitations:**
- RDTSC timing check (CPU timestamp counter behavior under
  virtualization) — not realistically fixable through `.vmx` settings.
- `vmci.sys` (VMware Tools driver) — removing it risks breaking
  VMware Tools functionality the project relies on for file transfer,
  so it was left in place.

## Behavioral hardening (not VM-specific)

Pafish/al-khaser also flagged sandbox-pattern behaviors unrelated to
virtualization itself — a freshly imaged or freshly booted machine
looks artificial regardless of environment:

- Missing mouse/click activity
- Missing or implausible dialog confirmation
- Low system uptime (`GetTickCount()`)

**Mitigation:** before each sample run, a short period of simulated
interaction (opening folders, a few clicks, a brief idle period) is
performed on both the VM guest and the OptiPlex, so this flag doesn't
disproportionately affect one environment just because it was more
recently re-imaged/reverted.

## Verification

Before and after this hardening work, Pafish and al-khaser were run
on both environments to produce a calibration baseline:

- `calibration/vm-baseline-before-hardening.txt`
- `calibration/vm-baseline-after-hardening.txt`
- `calibration/bare-metal-baseline.txt`

See `calibration/` for the full output and a before/after comparison.
