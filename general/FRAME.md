# Frame

## Data Bytes

All data bytes will be sent in 9-bit data mode.
This means that individual data bytes will have one start bit, 9 data bits, zero parity bits, and one stop bit.
Bit 9 HIGH will indicate **Start of Frame** (SOF) and will only be HIGH for the first byte of a data frame.

## Frame Layout

Each frame will consist of N data bytes (up to 256) with a maximum total frame length of 260 (N + 4).
Obviously the total length should be as short as possible.

| Address | Padding | Data Length | Data            | CRC16  |
| :-----: | :-----: | :---------: | :-------------: | :----: |
| <3:0>   | 0000    | <7:0>       | N \| N+1 \| N+2 | <15:0> |

### CRC calculation

This value will be computed only using the *Data* bytes in a data frame.
We will be using a CRC16 calculation with the USB CRC table.
Computations will be performed using the `crc` crate found [here](https://crates.io/crates/crc).
