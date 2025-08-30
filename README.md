# Subnetting Cheatsheet & Method

This repository contains a detailed, step-by-step guide for calculating IPv4 subnets, along with a brief explanation of what subnetting is and why it is a fundamental skill in computer networking.

---

## What is Subnetting?

Subnetting is the process of taking a large network and dividing it into smaller, more manageable sub-networks, or "subnets."

*Imagine a large office building (the main network). Instead of having one giant open floor where everyone works, you divide it into different departments like Sales, Engineering, and Marketing (the subnets). Each department is separate, but they are all still part of the same building and can communicate when needed. Subnetting does the same for a computer network.*

## Why Do We Use Subnetting?

Dividing a network is crucial for several reasons:

- **Security**: You can create barriers between subnets. If a security breach happens in one subnet (e.g., the guest Wi-Fi), it's much harder for it to spread to a more sensitive subnet (e.g., the server network).

- **Performance**: By reducing the size of a broadcast domain, you reduce unnecessary network traffic. When a device sends a broadcast message, it only goes to the devices within its own subnet instead of the entire network, which improves speed and reduces congestion.

- **Organization**: It allows for better organization of hosts. You can group devices by department, location, or function, making the network easier to manage and troubleshoot.

## Method, Proof & Tools

- **The "Magic Number" Method**: For a detailed, step-by-step guide, see the file: **[`subnetting_cheatsheet.md`](./subnetting_cheatsheet.md)**.

- **Proof of Mastery**: This repository includes a log of 30 solved problems with timings to demonstrate speed and accuracy. **[View Timed Problems](./examples/timed_problems.md)**.

- **Practice Problems**: To test your skills, you can generate unlimited examples at [subnetipv4.com](https://subnetipv4.com/).

- **Subnet Calculator**: For quick verification, use an online tool like the [IP Subnet Calculator](https://www.calculator.net/ip-subnet-calculator.html).
