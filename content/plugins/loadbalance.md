+++
title = "loadbalance"
description = "*loadbalance* acts as a round-robin DNS loadbalancer by randomizing the order of A and AAAA records  in the answer."
weight = 17
tags = [ "plugin", "loadbalance" ]
categories = [ "plugin" ]
date = "2017-10-20T08:48:19.239928"
+++
 
 See [Wikipedia](https://en.wikipedia.org/wiki/Round-robin_DNS) about the pros and cons on this
 setup. It will take care to sort any CNAMEs before any address records, because some stub resolver
 implementations (like glibc) are particular about that.

## Syntax

~~~
loadbalance [POLICY]
~~~

* **POLICY** is how to balance, the default is "round_robin"

## Examples

Load balance replies coming back from Google Public DNS:

~~~ corefile
. {
    loadbalance round_robin
    proxy . 8.8.8.8 8.8.4.4
}
~~~
