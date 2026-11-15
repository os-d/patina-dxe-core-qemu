# Compatibility Mode Test Binary

`patina_dxe_core_qemu_test.zip` contains Q35 x64 DEBUG and RELEASE EFI binaries
and PDB symbols only. It is not a complete replacement for the upstream release.

The binaries use Patina commit `ebdbade6467b46724f718279b49d73b3bbc34973`
from `https://github.com/os-d/patina`, pinned in Cargo.toml and Cargo.lock.

Build commands:

```bash
cargo make q35
cargo make q35-release
```

The ZIP root contains `debug/` and `release/`, matching the Q35 platform FDF.
This archive is for the temporary Ubuntu SSD DEBUG/RELEASE pipeline tests.