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

# Project exercises

Now that we know the basics of how network elements work, we can start solving
the exercises. Also, we will be introducing new concepts and elements as they
appear in the exercises like routers, switches, etc.

## Level 1

<details>
  <summary>Show level details</summary>

![Level 1](images/level1.png)

In this level, all we need to do is ensure that IP directions are in a valid
range, they have to be in the same network IP and we have to double check that
the IPs are valid and every value is between 0 and 255.

</details>

## Level 2

<details>
  <summary>Show level details</summary>

![Level 2](images/level2.png)

This level is a bit tricky, because there are some considerations we haven't
taken before. For example, every host in a network should have the same subnet
mask (it's not strictly necessary as we are only *splitting the room in X
parts* and should be fine as long as there are no overlaps, but it's a good rule
to follow).

Also, when we talked about how both ends of the host IP ranges are reserved, we
should have added other reserved addresses like the ones for private networks.

The range `127.0.0.1 - 127.255.255.255` is reserved for localhost, and it allows
the computer to communicate with itself. One example that we have seen in the
cursus is in the Born2BeRoot project, in which we configure a web server and use
the localhost IP to connect to it.

</details>

## Level 3

<details>
  <summary>Show level details</summary>

![Level 3](images/level3.png)

In this level, we see a switch for the first time. The switch allows us to
increase the number of the connected devices, but it doesn't have any interface,
it only distributes packages to its local network.

I like to think about it like a power strip, it connects multiple devices to a
common ground but it has no power until you plug it to an outlet.

For the next part, we have to calculate the IP addresses range given a subnet
mask. To do so, we take the subnet mask and invert it or sustract the zeros
part.

In this case, for 255.255.255.128 or `/25`, the range of valid IPs goes from
`x.x.x.0 - x.x.x.127` (x being the network address), so every connected device
is OK as long as it doesn't go out of this range and doesn't overlap with lower
and upper ends.

</details>

## Level 4

<details>
  <summary>Show level details</summary>



![Level 4](images/level4.png)


</details>

## Level 5

<details>
  <summary>Show level details</summary>

![Level 5](images/level5.png)


</details>

## Level 6

<details>
  <summary>Show level details</summary>

![Level 6](images/level6.png)


</details>

## Level 7

<details>
  <summary>Show level details</summary>

![Level 7](images/level7.png)


</details>

## Level 8

<details>
  <summary>Show level details</summary>

![Level 8](images/level8.png)


</details>

## Level 9

<details>
  <summary>Show level details</summary>

![Level 9](images/level9.png)


</details>

## Level 10

<details>
  <summary>Show level details</summary>

![Level 10](images/level10.png)


</details>
