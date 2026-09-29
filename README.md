# tiaportal-controlpump-V1

## Chuyển đổi ASCII ↔ HEX (`PLC_1/External source files/AsciiHex.scl`)

Cách thêm vào TIA Portal:
1. Project tree → PLC_1 → **External source files** → **Add new external file** → chọn `AsciiHex.scl`.
2. Chuột phải vào file → **Generate blocks from source**.
3. Gọi `"AsciiHex_Demo"();` trong OB1 `Main`, rồi đặt `"AsciiHex_Test".Execute := TRUE` bằng Watch table để thử.

| Block | Chức năng | Ví dụ |
|---|---|---|
| `ASCII_To_HexString` | Chuỗi ASCII → chuỗi HEX | `'AB1'` → `'414231'` (hoặc `'41 42 31'`) |
| `HexString_To_ASCII` | Chuỗi HEX → chuỗi ASCII | `'414231'` → `'AB1'` |
| `Bytes_To_HexString` | Mảng Byte → chuỗi HEX | `[16#0A,16#FF]` → `'0AFF'` |
| `HexString_To_Bytes` | Chuỗi HEX → mảng Byte | `'0AFF'` → `[16#0A,16#FF]` |

Mã lỗi trả về: `0` OK, `-1` ký tự không phải HEX, `-2` quá dài, `-3` số ký tự HEX lẻ, `-4` Count không hợp lệ.
Yêu cầu: S7-1500 hoặc S7-1200 FW ≥ V4.2 (do dùng `Array[*] of Byte`).
