# NetPractice

This project is about solving 10 networking problems to make a network run. We will
configure small networks, but first we must know how networking and IP addresses
work.

## Basic concepts

### TCP

TCP stands for *Transmission Control Protocol*, and guarantees communication
integrity between network clients. It divides data in small packages and checks
that every one of them have been received without errors.

### IP

IP stands for *Internet Protocol*, and it's a logical way of addressing every
device in a network. An IP has two parts, one identifies the host and the other
represents the net to which it belongs. To separate them, we use **subnet
masks**.

There are 2 versions of IP, IPv4 (uses 32 bits to represent the address) and
IPv6 (uses 128 bits). The main difference is the number of devices they can
address, 2^32 vs 2^128. In this project, we will only work with IPv4 addresses.

### Subnet mask

The subnet mask is a 32 bit address, and as we said on the IP definition, we use
subnet masks to separate between network and host address. A valid subnet mask,
represented in binary, must have from 1 to 32 ones in a row at the beginning and
the rest must be zeros.

Some examples of valid network masks and their binary form:

| Network mask  | Binary form                         |
|---------------|-------------------------------------|
| 255.128.0.0   | 11111111.10000000.00000000.00000000 |
| 255.255.255.0 | 11111111.11111111.11111111.00000000 |

Another way of representing subnet masks is the **CIDR notation**. It represents
the address with `/number_of_ones_in_a_row`. For example, the addresses in the
table can also be represented with `/9` and `/24` respectively.

## How to calculate network and host address range

Given an IP and a subnet mask, we will represent them both in binary form:

|             | IP                                  | Network Mask                        |
|-------------|-------------------------------------|-------------------------------------|
| Address     | 104.198.241.125                     | 255.255.255.0                       |
| Binary form | 01101000.11000110.11110001.01111101 | 11111111.11111111.11111111.00000000 |

To obtain the **network IP**, we must AND both binary addresses, resulting in
`01101000.11000110.11110001.00000000` or `104.198.241.0`.

To calculate the host address range, we take the last octet, in this case its
`00000000`. The host addresses can range between `00000000` and `11111111`,
translated to our example, the IPs can range between `104.198.241.0 -
104.198.241.255`.

We didn't mention it before, but **the ends of the range are reserved
addresses** and can't be used. The lower end is reserved for the network IP and
the upper end is the broadcast address, so the effective range is `104.198.241.0 - 104.198.241.255`.

