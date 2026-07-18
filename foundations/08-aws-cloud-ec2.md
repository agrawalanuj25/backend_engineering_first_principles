# 08 — AWS, the Cloud, and EC2 (Renting Computers)

> **Goal:** Understand what "deployed in AWS," "EC2 instance," and "public IP" mean in Video 3 — without the cloud jargon.

---

## Plain definition

- **The Cloud**: someone else's computers, rented over the internet. Instead of buying a server and putting it in your closet, you **rent** one from a company and access it online.
- **AWS (Amazon Web Services)**: the most popular cloud provider (owned by Amazon). It rents computers, storage, databases, and more.
- **EC2 (Elastic Compute Cloud)**: AWS's service for renting a **virtual computer** (a "virtual machine") that runs your software.
- **Instance**: one rented virtual computer. "An EC2 instance" = one rented machine.
- **Public IP**: the internet-facing address of that machine, so people can reach it.
- **Region vs Availability Zone**: a **Region** is a geographic area (e.g., `us-east-1`); distance from your users affects speed. Each Region *contains multiple* **Availability Zones (AZs)** — each AZ is one or more discrete data centers with independent power and networking. You spread a system across AZs so that one data center failing doesn't take you down (high availability).

---

## The apartment-rental analogy

| Cloud concept | Real-world equivalent |
|---------------|----------------------|
| Cloud provider (AWS) | A giant apartment company |
| EC2 instance | An apartment you rent |
| Public IP | Your apartment's street address |
| Region | The city the building is in |
| Availability Zone | A separate building in that city (if one loses power, others stay up) |
| You (SSH/login) | The tenant with a key |

You don't own the building; you rent an apartment, get an address, and run your stuff there. If you need a bigger one, you "upgrade" (more CPU/RAM).

---

## How Video 3 uses it

```mermaid
flowchart TD
    DNS[DNS: backend.demo.xyx -> IP] --> IP[(Public IP of EC2)]
    IP --> EC2[EC2 instance\n(a rented virtual computer in AWS)]
    EC2 --> APP[Your Node app on localhost:3001]
```

- The instructor **deployed** (uploaded & started) his backend on an EC2 instance.
- The EC2 has a **public IP** (from file 07's DNS A record).
- Requests from the internet arrive at that IP, then travel inside the machine to the app.

---

## Why rent instead of using your laptop?

| Your laptop | A cloud server (EC2) |
|-------------|----------------------|
| Only on when you're using it | Runs 24/7 |
| Public IP? Usually no (home network) | Yes — reachable worldwide |
| Power goes out → offline | In a data center with backup |
| Hard to scale | Click to add CPU/RAM |

For a real backend that serves users anytime, anywhere, you need a machine that's always on and publicly reachable — that's the cloud.

---

## "Deploy" — a key verb

**Deploy** = take your code from your laptop and put it on a server (like EC2) so other people can use it. Video 3's app is "deployed in AWS."

---

## Why this matters for the course

Almost every backend you'll build professionally runs on *someone's cloud* (AWS, Google Cloud, Azure, or similar). Video 3's AWS/EC2 demo is the standard real-world setup. Understanding "it's just a rented computer with a public IP" removes the mystery.

---

## Jargon table

| Term | Meaning |
|------|---------|
| Cloud | Renting someone else's computers over the internet |
| AWS | Amazon's cloud provider |
| EC2 | AWS service for renting virtual computers |
| Instance | One rented virtual machine |
| Public IP | The internet address of that machine |
| Region | The physical location of the data center |
| Deploy | Put your code on a server so others can use it |
| SSH | A way to log into a remote computer (port 22) |

---

## Key takeaways

1. **The cloud = rented computers** you reach over the internet.
2. **EC2 instance = one rented virtual machine** with a **public IP**.
3. Video 3's backend lives on an EC2 instance in AWS.

---

## Quick check

- Is "the cloud" a magical thing or just rented computers? *(rented computers)*
- In Video 3, what does the DNS A record point to? *(the EC2 instance's public IP)*

> Ask me before file 09 (firewalls & security groups).
