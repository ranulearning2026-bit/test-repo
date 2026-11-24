Batch: 69af653045f02c744886769d30c19c81c024f952
Updated: 2026-11-24T14:17:02Z
Source folder: src/nova/

## Totals

| Metric | Value |
|--------|------:|
| Tracked files | 2,256 |
| Source files (extractable) | 1,510 |
| OTHER files | 745 |
| UNKNOWN files | 1 |
| Total code lines (source) | 473,433 |
| Total comment lines (source) | 60,276 |
| Total blank lines (source) | 78,325 |
| Source files without `loc` | 0 |
| Change (files) vs. prev batch | +1,510 |
| Change (code lines) vs. prev batch | +473,433 |

## Lines of Code by Language

| Language | Files | Code | Comments | Blanks | % of Code |
|----------|------:|-----:|---------:|-------:|----------:|
| Python | 1,510 | 473,433 | 60,276 | 78,325 | 100.0% |
| **Total** | **1,510** | **473,433** | **60,276** | **78,325** | **100%** |

## Lines of Code by Component

| Component | Files | Code | Comments | Blanks | % of Code |
|-----------|------:|-----:|---------:|-------:|----------:|
| tests-unit | 514 | 250,429 | 17,443 | 39,122 | 52.9% |
| tests-functional | 314 | 58,483 | 13,098 | 11,879 | 12.4% |
| virt | 91 | 39,352 | 6,015 | 7,103 | 8.3% |
| api | 199 | 25,261 | 4,407 | 3,897 | 5.3% |
| compute | 25 | 21,716 | 4,725 | 2,982 | 4.6% |
| objects | 49 | 12,607 | 2,984 | 2,462 | 2.7% |
| conf | 48 | 8,914 | 762 | 491 | 1.9% |
| tests-fixtures | 16 | 8,729 | 996 | 1,246 | 1.8% |
| nova | 30 | 8,230 | 1,354 | 2,518 | 1.7% |
| db | 26 | 7,663 | 1,038 | 1,445 | 1.6% |
| scheduler | 41 | 6,575 | 1,705 | 1,093 | 1.4% |
| network | 6 | 4,371 | 870 | 693 | 0.9% |
| conductor | 9 | 4,136 | 1,086 | 462 | 0.9% |
| cmd | 12 | 3,767 | 764 | 498 | 0.8% |
| policies | 56 | 3,467 | 867 | 490 | 0.7% |
| pci | 7 | 2,079 | 393 | 301 | 0.4% |
| notifications | 18 | 1,736 | 638 | 376 | 0.4% |
| image | 2 | 951 | 132 | 166 | 0.2% |
| hacking | 2 | 903 | 71 | 166 | 0.2% |
| privsep | 8 | 800 | 262 | 260 | 0.2% |
| volume | 2 | 724 | 88 | 139 | 0.2% |
| console | 12 | 677 | 203 | 178 | 0.1% |
| limit | 4 | 432 | 127 | 98 | 0.1% |
| storage | 2 | 401 | 48 | 64 | 0.1% |
| accelerator | 2 | 346 | 26 | 47 | 0.1% |
| share | 2 | 305 | 12 | 45 | 0.1% |
| servicegroup | 6 | 220 | 104 | 57 | 0.0% |
| keymgr | 2 | 100 | 14 | 27 | 0.0% |
| tests | 2 | 37 | 18 | 10 | 0.0% |
| wsgi | 3 | 22 | 26 | 10 | 0.0% |
| **Total** | **1,510** | **473,433** | **60,276** | **78,325** | **100%** |

### Code Lines per Language by Component

| Component | Python |
|-----------|-------:|
| tests-unit | 250,429 |
| tests-functional | 58,483 |
| virt | 39,352 |
| api | 25,261 |
| compute | 21,716 |
| objects | 12,607 |
| conf | 8,914 |
| tests-fixtures | 8,729 |
| nova | 8,230 |
| db | 7,663 |
| scheduler | 6,575 |
| network | 4,371 |
| conductor | 4,136 |
| cmd | 3,767 |
| policies | 3,467 |
| pci | 2,079 |
| notifications | 1,736 |
| image | 951 |
| hacking | 903 |
| privsep | 800 |
| volume | 724 |
| console | 677 |
| limit | 432 |
| storage | 401 |
| accelerator | 346 |
| share | 305 |
| servicegroup | 220 |
| keymgr | 100 |
| tests | 37 |
| wsgi | 22 |

## Folder Structure

Source files only, two directory levels below `src/nova/`.

```
src/nova/
  (top-level modules)  8,230 lines, 30 files
  accelerator/  346 lines, 2 files
    (top-level modules)  346 lines, 2 files
  api/  25,261 lines, 199 files
    (top-level modules)  299 lines, 4 files
    metadata/  975 lines, 7 files
    openstack/  21,694 lines, 168 files
    validation/  2,293 lines, 20 files
  cmd/  3,767 lines, 12 files
    (top-level modules)  3,767 lines, 12 files
  compute/  21,716 lines, 25 files
    (top-level modules)  21,550 lines, 21 files
    monitors/  166 lines, 4 files
  conductor/  4,136 lines, 9 files
    (top-level modules)  2,362 lines, 4 files
    tasks/  1,774 lines, 5 files
  conf/  8,914 lines, 48 files
    (top-level modules)  8,914 lines, 48 files
  console/  677 lines, 12 files
    (top-level modules)  307 lines, 4 files
    rfb/  189 lines, 5 files
    securityproxy/  181 lines, 3 files
  db/  7,663 lines, 26 files
    (top-level modules)  221 lines, 5 files
    api/  1,074 lines, 7 files
    main/  6,368 lines, 14 files
  hacking/  903 lines, 2 files
    (top-level modules)  903 lines, 2 files
  image/  951 lines, 2 files
    (top-level modules)  951 lines, 2 files
  keymgr/  100 lines, 2 files
    (top-level modules)  100 lines, 2 files
  limit/  432 lines, 4 files
    (top-level modules)  432 lines, 4 files
  network/  4,371 lines, 6 files
    (top-level modules)  4,371 lines, 6 files
  notifications/  1,736 lines, 18 files
    (top-level modules)  263 lines, 2 files
    objects/  1,473 lines, 16 files
  objects/  12,607 lines, 49 files
    (top-level modules)  12,607 lines, 49 files
  pci/  2,079 lines, 7 files
    (top-level modules)  2,079 lines, 7 files
  policies/  3,467 lines, 56 files
    (top-level modules)  3,467 lines, 56 files
  privsep/  800 lines, 8 files
    (top-level modules)  800 lines, 8 files
  scheduler/  6,575 lines, 41 files
    (top-level modules)  3,026 lines, 6 files
    client/  2,145 lines, 3 files
    filters/  997 lines, 19 files
    weights/  407 lines, 13 files
  servicegroup/  220 lines, 6 files
    (top-level modules)  55 lines, 2 files
    drivers/  165 lines, 4 files
  share/  305 lines, 2 files
    (top-level modules)  305 lines, 2 files
  storage/  401 lines, 2 files
    (top-level modules)  401 lines, 2 files
  tests/  317,678 lines, 846 files
    (top-level modules)  37 lines, 2 files
    fixtures/  8,729 lines, 16 files
    functional/  58,483 lines, 314 files
    unit/  250,429 lines, 514 files
  virt/  39,352 lines, 91 files
    (top-level modules)  7,181 lines, 15 files
    disk/  1,245 lines, 10 files
    image/  90 lines, 2 files
    ironic/  2,214 lines, 4 files
    libvirt/  22,282 lines, 40 files
    vmwareapi/  5,763 lines, 15 files
    zvm/  577 lines, 5 files
  volume/  724 lines, 2 files
    (top-level modules)  724 lines, 2 files
  wsgi/  22 lines, 3 files
    (top-level modules)  22 lines, 3 files
```

## Growth History

| Batch | Date | Source Files | Code Lines | Change |
|-------|------|-------------:|-----------:|-------:|
| 69af6530 | 2026-11-24 | 1,510 | 473,433 | +473,433 |

## Notes

- **LOC** figures come from tokei output stored in the `loc` field of `.aee/intake.jsonl`. Source files without a `loc` entry are counted in file totals but excluded from all line counts.
- **Components** come from `.aee/components.json`.
- **UNKNOWN files**: `src/nova/tests/unit/ssl_cert/new_cert.sh`
