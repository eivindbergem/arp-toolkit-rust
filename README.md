# arp-toolkit [![crates.io](https://img.shields.io/crates/v/arp-toolkit.svg)](https://crates.io/crates/arp-toolkit)


Toolkit for (R)ARP , the `(Reverse) Address Resolution Protocol`. 

Supports simplified sending and receiving of (R)ARP requests/responses using an abstracted Client. Also allows easy manipulation and building of (R)ARP packets.

## Build
To build it, use
```
cargo build
```

**Note**: only the `async-example` is built per default. To build the `sync-example`, change to the directory and run `cargo build`. This is because sync and async can not be used in the same crate simultaneously.

## Usage
The `sync-example/sync-example.rs` file shows high-level usage of the class `ArpClient` using blocking IO. For example, it illustrates how to get the MAC address for the corresponding IP and vice versa with a single function call. `async-example/async-example.rs` shows the same, but with `async` IO.

It is also possible to directly send, receive and manipulate (R)ARP packages. To see how this works, take a look at the examples and the method `resolve_advanced`.

To use **blocking** IO instead of **async** IO, activate the feature `sync` in your `Cargo.toml` like this: 
```
[dependencies]
arp-toolkit = {version = x.x.x, features = ["sync"]}
```


**Important note**: As this library uses Raw sockets, either [set](https://squidarth.com/networking/systems/rc/2018/05/28/using-raw-sockets.html) the `CAP_NET_RAW` capability or run your program with `sudo`. (not recommended)

