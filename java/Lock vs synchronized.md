





> Impossible. It can be implemented in different ways, e.g., via the [Compare-and-swap](http://en.wikipedia.org/wiki/Compare-and-swap) where the hardware guarantees sequential execution. It can get a bit complicated in presence of multiple cores or even multiple sockets and needs a complicated [protocol](http://en.wikipedia.org/wiki/MESI_protocol) between the cores, but this is all taken care of.