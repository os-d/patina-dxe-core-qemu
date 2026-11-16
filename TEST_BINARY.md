# Compatibility Mode Final-State Test Binary

`patina_dxe_core_qemu_test.zip` contains Q35 x64 DEBUG and RELEASE EFI binaries
and PDB symbols only. It is not a complete replacement for the upstream release.

The binaries use Patina commit
`34cd4c398e3583aa1fa60760bbad16b8ed07c28a`. They bound compatibility updates
to the remaining descriptor/range intersection and activate global compatibility
only once, while retaining per-image mapping on every call. Temporary
`MEMWATCH` instrumentation has been removed. The source includes the
non-loader attribute preservation regression test.
Cargo.toml and Cargo.lock pin this published commit from the
`os-d/patina` fork.

Build commands:

```bash
cargo make q35
cargo make q35-release
```

The ZIP root contains `debug/` and `release/`, matching the Q35 platform FDF.
This archive is for the temporary Ubuntu SSD DEBUG/RELEASE pipeline tests.

Publish the updated ZIP before updating the QEMU external dependency URL and
SHA-256. Prefer an immutable raw GitHub commit URL, as in the earlier test.