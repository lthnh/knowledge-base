---
id: C28x_Assembly
aliases: []
tags: []
---
There are four main addressing modes in C28x assembly:
- Register: operate between registers
- Immediate (symbol: #): constants and initialization
- Direct (or paged, symbol: @): general purpose access to data
- Indirect (or pointer, symbol: *): support for pointers - access arrays, lists, tables

In register addressing mode, special characters (@, *, or #) are optional, according to [this link](https://e2e.ti.com/cfs-file/__key/communityserver-discussions-components-files/171/C28x-Workshop-_2D00_-apx-B-and-C.pdf).

In direct addressing mode, data memory space divided into 65,536 pages with 64 words per page. Data page pointer is DP. 16-bit DP is added to a 6-bit offset to form absolute 22-bit address.

Eight hardware pointers (ARs) can be used to access the first 64k of data memory. XAR registers are needed to access full 4 gigawords data space.
Indirect addresing mode is the best way to find CSM passwords.

