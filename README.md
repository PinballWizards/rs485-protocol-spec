# rs485-protocol-spec

This should be a space that describes the complete communication protocol in use for our capstone.

### goals

* determine bitrate
* extreme memory efficiency (do we serialize ourselves or use serde?)
  * write buffer is 16 bytes on atsamd21
* determine architecture (one master, many slaves or multi master)
  * determine when nodes can communicate
* extreme network efficiency
  * don't communicate more than necessary
  * handling sercom interrupts potentially takes away from processing time