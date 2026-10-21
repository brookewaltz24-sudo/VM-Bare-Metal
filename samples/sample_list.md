**No malware files are stored in this repository — hashes and metadata only.**

| ID | SHA256 | Filename | File Type | Tags | First Seen | VirusTotal Confirmed | Status | Notes |
|----|--------|----------|-----------|------|------------|------------------------|--------|-------|
| 001 | `0fa4177ccc1cc52febf7c54f98906a2bff941549473607c9e862333faea5ff05` | update.jar | jar/java | jvm-agent, runelite, runelure | 2026-10-06 | ⚠️ pending | ⚠️ pending | |
| 002 | `840244014ea8cfa9bcbfdbdc360b3a309ddea340fdf676a3ae26f806f97e21` | stage2_decoded.zip | zip | Astaroth, au3, banker, brasilengenharia, ecom-store, guildma, vmi3554028.con, taboserver-net | 2026-09-22 | ⚠️ pending | ⚠️ pending | |
| 003 | `8c382f17397517bda1ac66533c8c40c571e1ec078c84a4b2d397fa2f34bdd1c4` | AntiSkidDLL.dll | dll | antivm, roblox | 2026-09-21 | ⚠️ pending | ⚠️ pending | Strong match — explicit antivm tag |
| 004 | `cf0d4b3837b9a23fb46cbb0a90f5ecae6b7dcd5b1f13b9d4a5fe0de7cec85041` | RuntimeBroker.exe | exe | Loader, registry-persistence, RuntimeBroker, VMProtect, websocket-c2 | 2026-08-31 | ⚠️ pending | ⚠️ pending | VMProtect = packer, not confirmed anti-VM logic yet |
| 005 | `ceedf7563caa830f856d8da877da9834ab35ffeac38df1d7df87485682bf6f7` | Danilhex-Valhex.exe | exe | Generic, MalPack, packed, VMProtect | 2026-09-01 | ⚠️ pending | ⚠️ pending | |
| 006 | `128e4181c914a8d31bf910661a568189588c018ce11fe9065551f496ae06ce47` | 4vaUDxmDdJyt.exe | exe | Evader, VMProtect | 2026-09-12 | ⚠️ pending | ⚠️ pending | |
| 007 | `e500490fb15288bc3d7ce87eb571ac6a4f70cc27f90930c9dbc73e8706dbe2eb` | CloverGameInstaller.exe | exe | DataStealer, passwordstealer, Python, spyware, vmdetect | 2026-05-30 | ⚠️ pending | ⚠️ pending | Strong match — explicit vmdetect tag |
| 008 | `083354329045aba6279a288b567d09110c08dc14b0edb0ac099d01a1c0cb0ab` | GitSoftware.exe | exe | Generic, Lazy, MalPack, signed, VMProtect | 2026-06-20 | ⚠️ pending | ⚠️ pending | |
| 009 | `95ac4f25ca24aab7a5a443b813a3f92f0bbbc0a431e5e75764609f9214c114b3` | UpdaterSetup.exe | exe | antivm, backdoor, Downloader, dropper, vshell | 2026-07-29 | ⚠️ pending | ⚠️ pending | Strong match — explicit antivm tag |
| 010 | `9ef647a3c5ccfd56d445e0945ec4d6ba572e97a761327571daed1d8509d3a6c2` | 1488.exe | exe | Dacic, knotweed, packed, VMProtect | 2026-08-14 | ⚠️ pending | ⚠️ pending | |

## Legend
- ✅ confirmed — VirusTotal detection(s) confirm malicious classification and/or anti-VM/evasive behavior tags
- ❌ discarded — see `discard-log.csv` for reason
- ⚠️ pending — not yet checked

## Verification method
Each sample's SHA-256 is looked up on VirusTotal (virustotal.com) to confirm:
1. Multi-engine detection (sample is genuinely flagged as malicious, not a
   false/stale MalwareBazaar listing)
2. Reported behavior tags or sandbox summaries consistent with VM-aware/
   evasive behavior, where available

Note: VirusTotal confirms detection and reported behavior tags from its own
sandboxes/engines; it does not perform the static capability analysis that
a tool like capa does. Where deeper confirmation of anti-VM code is needed,
capa remains available as a secondary check.

## Reminder before use
Hashes above were reconstructed from a PDF export and should be
cross-checked against MalwareBazaar directly before relying on them
for sample retrieval or chain-of-custody records.
