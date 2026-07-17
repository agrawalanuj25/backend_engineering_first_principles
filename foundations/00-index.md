# Foundations — Start Here (Prerequisites for the Course)

> **Who is this for?** You said you're new to servers, Node, AWS, etc. The course videos (and the `notes/` folder) assume you already know these. This `foundations/` folder teaches those building blocks **from scratch** so the videos make sense.
>
> **How to use it:** Read the files **in order** (01 → 13). Each file explains one concept with a plain definition, a real-world analogy, a diagram, and a jargon table. After each, ask me any question you have. Don't move to the next file until the current one feels clear.
>
> **Relation to other folders:**
> - `notes/01-roadmap-notes.md` … = the course syllabus (advanced; read later).
> - `notes/03-what-is-backend.md` … = Video 3 notes (references everything below).
> - This folder = the **vocabulary** those notes assume.

---

## The Big Picture (how all these pieces fit)

When you watch Video 3, the instructor traces a request like this:

```mermaid
flowchart TD
    YOU[You + Browser on your laptop] -->|type URL| NET((Internet))
    NET --> DNS[DNS: translates name -> IP\n(file 07)]
    DNS --> CLOUD[AWS Cloud\n(file 08)]
    CLOUD --> EC2[EC2 = a rented computer\n(file 08)]
    EC2 --> FW[Firewall / Security Group\n(file 09)]
    FW --> NGINX[Reverse Proxy (Nginx)\n(file 10)]
    NGINX --> APP[Your app server\nNode.js (file 05)]
    APP --> DB[(Database)\n(file 12)]
    APP -. talks using .-> HTTP[HTTP messages\n(file 06)]
    NGINX -. encrypts with .-> TLS[HTTPS / TLS\n(file 11)]
    YOU -. runs code in .-> BROWSER[Browser sandbox\n(file 13)]
```

Every box above is one of the files below. Read them in order and the picture assembles itself.

---

## Reading Order

| # | File | What you'll understand |
|---|------|------------------------|
| 00 | `00-index.md` | This map (you are here) |
| 01 | `01-internet-networks-ip.md` | How computers talk across the world |
| 02 | `02-clients-servers-ports.md` | Server, client, port, localhost |
| 03 | `03-frontend-vs-backend.md` | The two halves of every web app |
| 04 | `04-code-language-runtime-framework.md` | Code, language, runtime, framework, library |
| 05 | `05-nodejs-and-servers.md` | Node.js + what "running a server" means |
| 06 | `06-http-basics.md` | Requests, responses, URLs, status codes |
| 07 | `07-dns-domains.md` | Domain names, DNS, subdomains |
| 08 | `08-aws-cloud-ec2.md` | Cloud, AWS, EC2 (rented computers) |
| 09 | `09-firewall-security-group.md` | Firewalls, security groups |
| 10 | `10-reverse-proxy-nginx.md` | Reverse proxy, Nginx |
| 11 | `11-https-ssl-tls.md` | Encryption, HTTPS, certbot |
| 12 | `12-databases-drivers-pools.md` | Databases, drivers, connection pools |
| 13 | `13-browser-sandbox-cors.md` | Browser runtime, sandbox, CORS, hydration |

---

## A 10-second mental model

> **The internet is a postal system for computers.** Your browser writes a "letter" (a request), addresses it with an IP/domain, and it travels through the internet to a **server** (a computer that waits for letters). The server reads it, does some work (maybe asks a **database**), writes back a "reply" (a response), and the letter comes home to your browser.

Everything in this folder is just explaining the parts of that sentence.

---

## Study tip

After reading a file, try to **explain it in one sentence to an imaginary friend**. If you get stuck, that's your question to ask me. I'll answer, then you move on.
