# The "Magic Number" Method — A Quick Way to Subnet

This method uses a simple process to quickly find the **Network Address**, **Broadcast Address**, and **Usable Host Range** for any given IPv4 address and CIDR prefix.

---

## The 4-Step Process

**Example IP:** `172.16.101.200 /22`

### Step 1 — Find the *Significant Octet*
Based on the CIDR prefix (`/p`), determine which octet contains the boundary between the network portion and the host portion (the *significant octet*):

- `/1` to `/8`  → first octet  
- `/9` to `/16` → second octet  
- `/17` to `/24` → third octet  
- `/25` to `/32` → fourth octet

For `172.16.101.200 /22`, the significant octet is the **third** (`101`).

---

### Step 2 — Find the *Magic Number* (Block Size)
The Magic Number is the subnet block size in the significant octet.

**Formula:**  
Magic Number = 256 - [Subnet mask value in the significant octet]

Quick reference (CIDR groups → mask value in that octet):

/8, /16, /24 : 255
/9, /17, /25 : 128
/10, /18, /26 : 192
/11, /19, /27 : 224
/12, /20, /28 : 240
/13, /21, /29 : 248
/14, /22, /30 : 252
/15, /23, /31 : 254

For `/22`, the mask value in the third octet is `252`.  
So the Magic Number is: `256 - 252 = 4`.

---

### Step 3 — Find the Network and Broadcast Addresses
**Network Address:** find the multiple of the Magic Number that is ≤ the value of the significant octet. Replace the significant octet with that multiple and set all subsequent octets to `0`.

- Significant octet value: `101`  
- Multiples of `4`: `..., 96, 100, 104, ...`  
- Closest multiple ≤ 101 is `100`.

**Network Address:** `172.16.100.0`

**Broadcast Address:** the next network would start at `172.16.104.0`. The broadcast address is the IP immediately before that, with all host bits set to `1`.

- Next network: `172.16.104.0`  
- **Broadcast Address:** `172.16.103.255`

---

### Step 4 — Find the Usable Host Range
- **First usable host:** Network + 1 → `172.16.100.1`  
- **Last usable host:** Broadcast - 1 → `172.16.103.254`

---

## Summary for `172.16.101.200 /22`
- **Network Address:** `172.16.100.0`  
- **Broadcast Address:** `172.16.103.255`  
- **First Usable Host:** `172.16.100.1`  
- **Last Usable Host:** `172.16.103.254`  
- **Total Hosts:** `2^(32-22) = 1024`  
- **Usable Hosts:** `1024 - 2 = 1022`

---

