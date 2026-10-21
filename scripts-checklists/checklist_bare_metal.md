### Before the run
- [ ] No network cable connected (isolated switch only, or confirmed
      disconnected)
- [ ] Image drive and boot USB physically unplugged
- [ ] Restored from checksum-verified Clonezilla image
- [ ] Restored partitions hash-verified against baseline, before boot
- [ ] Defender exclusions confirmed present for tools folder
- [ ] Sample SHA-256 verified immediately before this run
- [ ] Sample loaded via write-protected USB, USB removed after transfer

### During the run
- [ ] FakeNet-NG running (single-host mode)
- [ ] Procmon running (background capture to file)
- [ ] Regshot pre-shot taken
- [ ] Sample executed
- [ ] Fixed run duration observed (45 minutes, matches VM side)

### After the run
- [ ] Regshot post-shot taken
- [ ] Autorunsc run and exported
- [ ] FakeNet-NG and Procmon captures stopped
- [ ] Procmon exported to CSV (inside Windows, before shutdown)
- [ ] Machine shut down
- [ ] Linux live USB booted, disk mounted read-only
- [ ] Only text-based logs copied to log-out USB
- [ ] Completion state classified
- [ ] Results recorded in comparison table
- [ ] Clonezilla image restored again before next sample
