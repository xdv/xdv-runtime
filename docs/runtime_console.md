# runtime_console

- Source: `xdv-runtime/src/runtime_console.ds`
- Kind: Runtime Module
- Summary: Runtime Console - Console I/O

## Purpose
Runtime Console - Console I/O

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `RuntimeConsole` | 32 | 9 |
| `RuntimeConsoleErrors` | 4 | 0 |

## API By Forge
### RuntimeConsole

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `putchar` | `ch: UInt8` | `UInt32` | Performs putchar operation. |
| `K` | `puts` | `ptr: UInt64` | `UInt32` | Performs puts operation. |
| `K` | `getchar` | `(none)` | `UInt32` | Performs getchar operation. |
| `K` | `clear` | `(none)` | `UInt32` | Performs clear operation. |
| `K` | `set_cursor` | `row: UInt32, col: UInt32` | `UInt32` | Performs set cursor operation. |
| `K` | `get_cursor_row` | `(none)` | `UInt32` | Performs get cursor row operation. |
| `K` | `get_cursor_col` | `(none)` | `UInt32` | Performs get cursor col operation. |
| `K` | `scroll` | `(none)` | `UInt32` | Performs scroll operation. |
| `K` | `set_color` | `fg: UInt8, bg: UInt8` | `UInt32` | Performs set color operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `VGA_ADDR` | `UInt64` | `18432` |
| `VGA_WIDTH` | `UInt32` | `80` |
| `VGA_HEIGHT` | `UInt32` | `25` |
| `VGA_SIZE` | `UInt32` | `4000` |
| `COLOR_BLACK` | `UInt8` | `0` |
| `COLOR_BLUE` | `UInt8` | `1` |
| `COLOR_GREEN` | `UInt8` | `2` |
| `COLOR_CYAN` | `UInt8` | `3` |
| `COLOR_RED` | `UInt8` | `4` |
| `COLOR_MAGENTA` | `UInt8` | `5` |
| `COLOR_BROWN` | `UInt8` | `6` |
| `COLOR_LIGHT_GRAY` | `UInt8` | `7` |
| `COLOR_DARK_GRAY` | `UInt8` | `8` |
| `COLOR_LIGHT_BLUE` | `UInt8` | `9` |
| `COLOR_LIGHT_GREEN` | `UInt8` | `10` |
| `COLOR_LIGHT_CYAN` | `UInt8` | `11` |
| `COLOR_LIGHT_RED` | `UInt8` | `12` |
| `COLOR_LIGHT_MAGENTA` | `UInt8` | `13` |
| `COLOR_YELLOW` | `UInt8` | `14` |
| `COLOR_WHITE` | `UInt8` | `15` |
| `SERIAL_TX_PORT` | `UInt16` | `1016` |
| `KEYBOARD_RX_PORT` | `UInt16` | `960` |
| `CURSOR_ROW_PORT` | `UInt16` | `980` |
| `CURSOR_COL_PORT` | `UInt16` | `981` |
| `CURSOR_CMD_PORT` | `UInt16` | `982` |
| `COLOR_PORT` | `UInt16` | `983` |
| `SCROLL_PORT` | `UInt16` | `984` |
| `IO_OK` | `UInt32` | `0` |
| `CURSOR_COMMIT` | `UInt8` | `1` |
| `SCROLL_LINE` | `UInt8` | `1` |
| `CURSOR_LAST_ROW` | `UInt32` | `24` |
| `CURSOR_LAST_COL` | `UInt32` | `79` |

### RuntimeConsoleErrors

#### Procedures
- No `proc` entries in this forge.

#### Constants
| Constant | Type | Value |
|---|---|---|
| `ERR_OK` | `UInt32` | `0` |
| `ERR_INVALID_COORD` | `UInt32` | `1` |
| `ERR_OUT_OF_RANGE` | `UInt32` | `2` |
| `ERR_DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |

## Runtime Dependencies
- Detected dependency call usage:
- `console_init(...)`
- `display_line(...)`
- `io_read(...)`
- `io_write(...)`

## Integration Notes
- Runtime modules provide K-domain implementation with Q/Phi behavior gated by runtime availability policy where applicable.
- This module is intended for production runtime linkage and direct use by xdv-os components.

## Example (DPL)
```dust
let status = putchar(0);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
