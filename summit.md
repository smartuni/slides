class: center, middle, riot

# RIOT Summit 2016

## Using CoAP with RIOT

Lennart Dührsen, Raphael Hiesgen, Sebastian Meiling, Lotte Steenbrink

![:scale 50%](img/riot.png)

---

# disclaimer

* sharing our experience on using IoT technologies

* very subject to personal opinions

* not about bashing, no offense

---

# microcoap

* [https://github.com/1248/microcoap]()
    - seems abandoned, no reaction to PRs
    - several forks, e.g. [https://github.com/i2ot/microcoap]()

* really small, plain packet handler

* server-side only, no sending requests

* only core functions: GET, PUT, POST

* virtually no documentation, except the code itself

---

# libcoap

* full (?) featured CoAP implementation
    - client + server side
    - supports OBSERVE

* lots of dependencies, e.g., to build docs
    - _annoying_ when building with default config on RasPi
    - better build with: `./configure --disable-documentation`

* limited documentation and code examples
    - client example > 1000 LOCs
    - getting better, see [https://libcoap.net/]()

* `coap-client` useful for testing

---

# aiocoap

* Python 3, full (?) featured CoAP implementation

* issue: cannot handle interface identifiers
    - no link local IPv6 addresses
    - e.g., `[fe80::a:b:c:d%lowpan0]`
    - libcoap will do

* otherwise simple usage:

```python
from aiocoap import *

protocol = yield from Context.create_client_context()
req_temperature = Message(code=GET)
req_temperature.set_request_uri('coap://'[2001:db09::1]'/temperature')
res_temperature = yield from protocol.request(req_temperature).response
print(res_temperature.payload.decode('utf-8'))
```

---

# demo

* CoAP server
    - PhyTec PhyNode running RIOT with
    - [https://github.com/RIOT-Makers/climote]()

* 6LoBR/gateway
    - Raspberry Pi with OpenLabs transceiver
    - latest Raspbian with custom Linux-Kernel 4.7.y
    - RADVD, linux-wpan fork, 6lowpan branch [https://github.com/linux-wpan/radvd]
    - [https://github.com/raspberrypi/linux]()
    - [https://github.com/RIOT-Makers/wpan-raspbian]

* CoAP client
    - MacBook, OSX via ethernet
    - Firefox Copper
    - Python CoAP client
    - Wireshark, CC2531 sniffer

---

class: center, middle, riot
[![:scale 100%](img/riot.png)](http://www.riot-os.org)
## [www.riot-os.org](http://www.riot-os.org)
