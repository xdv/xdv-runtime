# runtime_fs

- Source: `xdv-runtime/src/runtime_fs.ds`
- Kind: Runtime Module
- Summary: Runtime file-system wrapper surface.

## Notes
This module uses parser-safe proc identifiers:
- `open_file(...)`
- `read_file(...)`
- `write_file(...)`
- `close_file(...)`
- `unlink_path(...)`

Other APIs retained:
- `mount(...)`, `umount(...)`
- `stat(...)`, `mkdir(...)`, `rmdir(...)`, `readdir(...)`
- `is_supported_flag(...)`