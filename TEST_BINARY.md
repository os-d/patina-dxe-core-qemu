# Memory Lifetime Diagnostic Test Binary

`patina_dxe_core_qemu_test.zip` contains Q35 x64 DEBUG and RELEASE EFI binaries
and PDB symbols only. It is not a complete replacement for the upstream release.

The binaries use Patina commit
`87928c54d53f5976258dd4a93f445cc9931681a4`. They bound compatibility updates
to the remaining descriptor/range intersection and activate global compatibility
only once, while retaining per-image mapping on every call. They retain
allocation-free `MEMWATCH` diagnostics for
the page at `0x27e902000`, containing the previous fault address `0x27e902048`.
Cargo.toml and Cargo.lock pin this published diagnostic commit from the
`os-d/patina` fork.

Build commands:

```bash
cargo make q35
cargo make q35-release
```

The ZIP root contains `debug/` and `release/`, matching the Q35 platform FDF.
This archive is for the temporary Ubuntu SSD DEBUG/RELEASE pipeline tests.

Pool allocations, pool frees, page-free requests, paging-attribute requests,
successful maps, and both unmap paths are logged when their ranges overlap
the watched page. Allocation/free and pre-unmap logs include stack traces.
No diagnostic heap buffers, memory-map queries, or page-table queries are
added. Code size and logging timing can still affect layout and reproduction;
check the next fault address if the watched page no longer matches.

Publish the updated ZIP before updating the QEMU external dependency URL and
SHA-256. Prefer an immutable raw GitHub commit URL, as in the earlier test.