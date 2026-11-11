# Sample Log

Samples sourced from MalwareBazaar for the VM vs. bare-metal comparison.

**No malware files are stored in this repository. Hashes and metadata only.**

| ID | SHA256 | File Name | File Type | Tags | First Seen | VM Progress | Bare-Metal |
|----|--------|-----------|-----------|------|------------|----------|
| 001 | `08f52a82b862ff7b8057f69a6214b087ea2d4fc44ac9fc3ed1a279791545c625` | 2025.10.22名单公布. | .exe | anti-vm, backdoor, SilverFox, ValleyRAT | 2025-10-23 | ✅ Done | ✅ Done |
| 002 | `68377a15f72e65bae234933695f920776ae9438a166c628af62e32452ad7ab74` | 过滤 | .exe | anti-vm, backdoor, injector | 2025-10-06 | ✅ Done | ✅ Done |
| 003 | `3050a5206d0847d5cfa16e79944ce348db688294e311db4d7b6045ffbe337450` | Qgwwal | .exe | Loader, PureLogs, PureLogsStealer, VMDetectloader | 2025-09-18 | ✅ Done | ✅ Done |
| 004 | `336e6c683d014775b1e9fc5e9953f5ae01d240969adc652705a7ddb1ba744a81` | escsvc | .exe | anti-vm, backdoor, dropper, signed, SilverFox, ValleyRAT | 2025-09-10 | ✅ Done | ✅ Done |
| 005 | `22c9c1e2f9d52fee918155e777686ba2f0c6fbd90e581832278af5d4de746dea` | main_kahre | .exe | anti-vm, injector, Loader, msvc, multiablo, process-hollowing | 2026-08-30 | ✅ Done | ✅ Done |
| 006 | `cdf92c4151397f89ca1ffec4e938c78059d9197f29895d1a9b6157013ab1ecc7` | Notepad++ | .exe | anti-vm, dropper, FakeApp, SilverFox, ValleyRAT | 2025-11-14 | ✅ Done | ✅ Done |
| 007 | `e500490fb15288bc3d7ce87eb571ac6a4f70cc27f90930c9dbc73e8706dbe2eb` | CloverGameInstaller | .exe | DataStealer, passwordstealer, Python, spyware, vmdetect | 2026-05-30 | ✅ Done | ✅ Done|
| 008 | `8ea162faea2475ecb14c4ef86ed7f24fe56b7b9b6540cc743136fa8cd816d6f6` | 红莲天刀 | .exe | anti-vm, backdoor, Downloader, dropper, flystudio | 2025-11-10 | ➕ Extra |
| 009 | `95ac4f25ca24aab7a5a443b813a3f92f0bbbc0a431e5e75764609f9214c114b3` | UpdaterSetup | .exe | anti-vm, backdoor, Downloader, dropper, vshell | 2026-07-29 | ✅ Done | ✅ Done |
| 010 | `350be6dedca5632a6ed7164c160480fe009707646e02256704ddd3c92c7a3edc` | updhost | .exe | anti-vm, backdoor, RustyStealer | 2025-10-28 | ➕ Extra |

## Legend
- ✅ Done: run completed in the environment(s) tested
- 🔄 In progress: currently being run
- ➕ Extra: spare candidate, used only to replace a discarded sample

## Notes
- All samples are plain `.exe` files, so they execute directly without an interpreter.
- Every sample carries an explicit `anti-vm` / `vmdetect` / `VMDetectloader` tag, or is an injector/loader with VM-aware behavior.
- Hashes are verified against MalwareBazaar and re-checked on the analysis machine immediately before each run.
- Discarded samples are logged with reasons in `samples/discard-log.csv`.
