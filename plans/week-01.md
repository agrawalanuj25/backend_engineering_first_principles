# Week 01 — Execution Plan

> **This is the route, not the map.** [`ROADMAP.md`](../ROADMAP.md) is the strategy
> (two tracks, the whole mountain). This file is what you actually *do* Monday
> through Sunday. Ignore Tracks 2/3 as "now" — they are the horizon. This week
> serves exactly one milestone.

**Profile this plan is tuned for:** ~1–2 focused hours/day · knows C++ (basic
loops + normal algos/LeetCode), **not** C · balanced applied+systems for momentum.

> **You are not learning C this week.** The socket calls (`socket`, `bind`,
> `listen`, `accept`, `recv`, `send`) are an **operating-system API**, not a
> language — you call them *identically* from C++. You'll write `.cpp`, compile
> with `g++`, use the C++ you already know. The only genuinely new things are
> three **systems** concepts — **pointers, structs, and file descriptors** — and
> you need those for HFT anyway (HFT *is* close-to-metal C++). Nothing wasted.
> The echo-server source in the appendix is verified to compile clean as C++.

**The one goal of Week 1 (Phase 0 milestone):**

> Draw a request's full path from browser to your handler and back, name every
> hop, **and prove one hop works** by writing the smallest program that speaks
> TCP.

You end the week with **two artifacts**: a working TCP echo server in C (systems
track) and a started `kb/02-http.md` (applied track). That's it. No fluff.

---

## How to use this file

- Each day = **one core block** (fits 1–2 hrs). Do the core; skip the *stretch*
  if you're short on time — it's optional depth, never a dependency.
- **Done when** is the pass/fail bar. If you can't tick it, don't advance —
  ask me instead. Falling a day behind is fine; skipping the "Done when" is not.
- Every day ends with a **self-check** you answer *out loud, from memory*. If you
  fumble it, that's the exact question to bring to me. (This is the Socratic
  loop — I'll keep asking "and then?" until it's airtight.)
- The C toolchain setup and full echo-server source are in the
  [Appendix](#appendix) — you are not expected to write C from a blank page.

Progress log at the bottom — tick each day so we stay in sync.

---

## Day 1 — The whole picture, from memory · *applied*

**Why:** the single mental model everything else hangs off. If the request path
is solid, every later topic is just "zoom into one box."

**Do:**
1. Read [`kb/01-what-is-a-backend.md`](../kb/01-what-is-a-backend.md) end to end (§1–§5 carefully).
2. Look at the diagram in [`foundations/00-index.md`](../foundations/00-index.md).
3. Close both files. On paper, **draw the path**: browser → DNS → (cloud/EC2) →
   firewall → reverse proxy → app server → DB, and the response coming back.
   Label each hop with one word on *what it does*.

**Done when:** you can draw the path from memory and name **≥ 6 hops** without
peeking, and say in one sentence what each does.

**Self-check (out loud):** "Why does the request *not* go straight to my
handler? Name three things standing in the way and what each is for."

*Stretch:* read `kb/01` §8 (senior pitfalls). Don't try to understand it — just
read it once so the vocabulary (HOL blocking, tail latency, CAP) starts to feel
familiar. It's your semester-end checklist.

---

## Day 2 — Finish the vocabulary · *applied*

**Why:** the playlist and notes *assume* these words. Close the gap now so
nothing later is blocked on "what's a reverse proxy again?"

**Do:**
1. Read whichever of [`foundations/`](../foundations/) `01 → 15` you haven't yet,
   **in order**. Don't linger — these are vocabulary, not deep dives.
2. As you go, keep a scratch list: for **DNS, TLS/HTTPS, reverse proxy (nginx),
   connection pool, CORS**, write *one sentence each* in your own words.

**Done when:** your 5 one-sentence definitions exist and don't just parrot the
file — they're in your words.

**Self-check:** "A reverse proxy and a load balancer — what's the overlap, and
what's the difference?" (If unsure, that's a question for me.)

---

## Day 3 — What the server *runs on* · *systems (OS)*

**Why:** your weakest lever per the roadmap, and the highest long-term payoff.
Start gentle: just the vocabulary of the machine.

**Do:**
1. Read **OSTEP** (free: <https://pages.cs.wisc.edu/~remzi/OSTEP/>) —
   **Ch 2 "Introduction to Operating Systems"** and **Ch 4 "The Abstraction: The
   Process."** ~30 pages, very readable. Skim Ch 5 (Process API: `fork`/`exec`).
2. Write down, in your words: **program vs process vs thread**, and **what a
   system call is** (why does calling the OS cost more than calling a function?).

**Done when:** you can explain process vs thread in 3 sentences, and say what
crosses the user↔kernel boundary on a system call.

**Self-check:** "When your server calls `recv()` to read from a socket, why is
that a *system call* and not just a normal function call? What does the CPU do
differently?"

*Stretch:* skim OSTEP Ch 6 (Limited Direct Execution) for the mode-switch
mechanism. This is the real answer to the self-check.

---

## Day 4 — HTTP on the wire · *applied (sets up kb/02)*

**Why:** HTTP is the protocol every request speaks. Today you *see the actual
bytes* instead of trusting a framework's `req` object.

**Do:**
1. Watch playlist **V5 "Understanding HTTP"** (or read MDN's *HTTP overview* +
   *HTTP messages* if you prefer text).
2. Run a real exchange and read it raw:
   ```bash
   curl -v https://example.com
   ```
   Identify in the output: the **request line** (method + path + version), the
   **request headers**, the blank line, then the **status line**, **response
   headers**, and **body**.
3. In `notes/`, jot the parts of an HTTP message and 5 status codes you should
   know cold (200, 301, 400, 401, 404, 500 — pick any 5 and say when each fires).

**Done when:** you can point at `curl -v` output and label request line / headers
/ status line / body, and explain what `Host:` and `Content-Type:` are for.

**Self-check:** "What's the difference between `401` and `403`? Between `301` and
`302`? Between `PUT` and `POST`?"

---

## Day 5 — What a socket *is* + get C compiling · *systems (setup day)*

**Why:** tomorrow you write a TCP server. Today = zero-risk setup so tomorrow is
pure payoff. No server yet.

**Do:**
1. Do the **toolchain check** in the [Appendix](#a-toolchain-setup). Compile and
   run the 3-line `hello.cpp` with `g++` (already installed on your machine).
2. Read **Beej's Guide** (<https://beej.us/guide/bgnet/>) — the sections *"What
   is a socket?"* and *"Structs"* (skim). It's written in C, but every call is
   the same from C++; just read past the `printf`s.
3. Learn the **5-call skeleton** conceptually — what each does, in one line:
   `socket()` → `bind()` → `listen()` → `accept()` → `recv()`/`send()`.
4. Meet the three new *systems* words: a **file descriptor** (a small int the OS
   hands you to name an open connection/file), a **struct** (a plain bundle of
   fields — here `sockaddr_in` holds an IP + port), and a **pointer** (`&x` = the
   address of `x`, which is how you hand a struct to an OS call). That's the
   whole "not-C++" surface for tomorrow.

**Done when:** `hello.cpp` compiled and ran, and you can recite the 5 socket
calls in order and say what a file descriptor is.

**Self-check:** "A server has *one* IP and *one* port (say :8080). How does it
hold thousands of simultaneous connections on it without them colliding?"
(Hint: it's in `kb/01`'s Socket row — the 4-tuple. Sit with this; it's the whole
trick of TCP.)

---

## Day 6 — The TCP echo server (the payoff) · *systems*

**Why:** this one exercise demystifies half of backend. After today, nginx and
Node stop being magic — they're this, scaled up.

**Do:**
1. Type out `echo_server.cpp` from the [Appendix](#c-tcp-echo-server-source) —
   **type it, don't paste**; the point is your fingers learning the calls.
2. Compile and run:
   ```bash
   g++ echo_server.cpp -o echo_server && ./echo_server
   ```
3. In a second terminal, connect and talk to it:
   ```bash
   nc localhost 8080      # type a line, press enter — it echoes back
   ```
4. Watch the server print the client's IP:port on connect. That printed port is
   half of the 4-tuple from yesterday — *seeing it is the aha.*

**Done when:** you type a line into `nc`, it echoes back, and the server logs the
client's ephemeral port. You can point to the line that does the echo (`send`
of what `recv` returned).

**Self-check:** "If a second `nc` connects while the first is still open, what
happens with *this* server — and why? What would you need to change to serve both
at once?" (This is the doorway to threads / `epoll` — Week 2.)

---

## Day 7 — Consolidate + teach it back · *both tracks*

**Why:** the non-negotiable loop is *learn → build → write it up → get quizzed.*
Passive input doesn't stick; producing does.

**Do:**
1. Start [`kb/02-http.md`](../kb/) using Day 4's material. Match the `kb/01`
   structure — at minimum get through: TL;DR → problem → mental model → core
   concepts table → **beginner pitfalls**. (Full pitfalls ladder + "how
   frameworks hide this" can finish next week — but start it.)
2. Update [`kb/README.md`](../kb/README.md): flip `02-http.md` from `planned` to
   `partial`.
3. **Teach-back:** answer this week's 6 self-checks out loud, from memory, as if
   to an interviewer. Note which two were shakiest.

**Done when:** `kb/02-http.md` exists with the first 5 sections, README updated,
and you've done the verbal teach-back.

**Self-check (the week's capstone):** *"You type a URL and press enter. Walk me
from keystroke to pixels — and I'll keep asking 'and then?'"* Get as far as you
can; where you stall is Week 2's syllabus.

---

## End-of-week: you can now…

- [ ] Draw the full request path and name every hop (Phase 0 milestone ✔)
- [ ] Read raw HTTP and label every part of a request/response
- [ ] Explain process vs thread and what a system call costs
- [ ] Explain how one IP:port serves thousands of connections (the 4-tuple)
- [ ] **Show a working TCP server you wrote** and explain every line
- [ ] Point at `kb/02-http.md` you started

If ≥ 5 of those tick, Week 1 succeeded. Bring me the two shaky self-checks and
we drill them before Week 2.

---

## Progress log (tick as you go — keeps us in sync)

| Day | Topic | Done? | Shaky on / questions |
|-----|-------|-------|----------------------|
| 1 | Request path from memory | ☐ | |
| 2 | Foundations vocabulary | ☐ | |
| 3 | OSTEP: process & syscall | ☐ | |
| 4 | HTTP on the wire | ☐ | |
| 5 | Sockets concept + C setup | ☐ | |
| 6 | TCP echo server | ☐ | |
| 7 | kb/02-http + teach-back | ☐ | |

---

## Appendix

### A. Toolchain setup

You already have `g++` (verified: 13.3). Confirm:
```bash
g++ --version        # any recent g++ is fine
```
If somehow missing on Debian/Ubuntu:
```bash
sudo apt update && sudo apt install -y build-essential
```
Then verify with a hello world — save as `hello.cpp`:
```cpp
#include <iostream>
int main() { std::cout << "toolchain works\n"; return 0; }
```
```bash
g++ hello.cpp -o hello && ./hello   # should print: toolchain works
```

You'll also want `nc` (netcat) for Day 6 — it's almost always preinstalled;
test with `nc -h`. If missing: `sudo apt install -y netcat-openbsd`.

### B. Reading list for the week (canonical, not blogs)

- **OSTEP** — <https://pages.cs.wisc.edu/~remzi/OSTEP/> (Ch 2, 4; skim 5, 6)
- **Beej's Guide to Network Programming** — <https://beej.us/guide/bgnet/>
- **MDN HTTP** — <https://developer.mozilla.org/en-US/docs/Web/HTTP> (overview + messages)
- Playlist V5 "Understanding HTTP" (Sriniously, *Backend from First Principles*)

### C. TCP echo server source

A minimal, single-connection, blocking echo server. **Verified to compile clean
as C++** (`g++ -Wall -Wextra echo_server.cpp -o echo_server`, zero warnings).
The socket calls are the same OS API you'd use from C — you're just writing C++.
**Type it out** rather than pasting — comments explain each call so you
understand, not memorize.

```cpp
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>       // close()
#include <arpa/inet.h>    // htons(), inet_ntoa()
#include <sys/socket.h>   // socket(), bind(), listen(), accept()

int main(void) {
    // 1. socket(): ask the OS for a TCP (SOCK_STREAM) IPv4 (AF_INET) endpoint.
    //    Returns a file descriptor — a small int the OS hands you to refer to it.
    int listen_fd = socket(AF_INET, SOCK_STREAM, 0);
    if (listen_fd < 0) { perror("socket"); exit(1); }

    // Let us re-run immediately after Ctrl-C without "address already in use".
    int opt = 1;
    setsockopt(listen_fd, SOL_SOCKET, SO_REUSEADDR, &opt, sizeof(opt));

    // Describe the address to listen on: any local interface, port 8080.
    struct sockaddr_in addr;
    memset(&addr, 0, sizeof(addr));
    addr.sin_family      = AF_INET;
    addr.sin_addr.s_addr = htonl(INADDR_ANY);  // 0.0.0.0 — any interface
    addr.sin_port        = htons(8080);        // htons: host->network byte order

    // 2. bind(): claim that IP:port for this socket.
    if (bind(listen_fd, (struct sockaddr *)&addr, sizeof(addr)) < 0) {
        perror("bind"); exit(1);
    }

    // 3. listen(): mark the socket passive — willing to accept connections.
    //    16 = backlog: how many pending connections the OS queues for us.
    if (listen(listen_fd, 16) < 0) { perror("listen"); exit(1); }

    printf("listening on :8080  (connect with: nc localhost 8080)\n");

    for (;;) {
        struct sockaddr_in client;
        socklen_t clen = sizeof(client);

        // 4. accept(): block until a client connects; returns a NEW fd for
        //    THIS connection. listen_fd keeps listening; conn_fd is the pipe
        //    to this one client. (This new fd is why one port serves many.)
        int conn_fd = accept(listen_fd, (struct sockaddr *)&client, &clen);
        if (conn_fd < 0) { perror("accept"); continue; }

        printf("client connected: %s:%d\n",
               inet_ntoa(client.sin_addr), ntohs(client.sin_port));

        // 5. recv()/send(): read bytes, write the same bytes back — "echo".
        //    recv returns 0 when the client closes; <0 on error.
        char buf[1024];
        ssize_t n;
        while ((n = recv(conn_fd, buf, sizeof(buf), 0)) > 0) {
            send(conn_fd, buf, n, 0);   // <-- THE echo: send back what we read
        }

        close(conn_fd);
        printf("client disconnected\n");
    }
    return 0;   // never reached
}
```

**The thing to notice:** `accept()` hands back a *new* fd per client, while
`listen_fd` keeps listening. That new fd is the OS-side of the unique 4-tuple
(your IP:8080 + their IP:ephemeral-port) — the exact mechanism from Day 5's
self-check. This single loop also handles **one client at a time** (it's blocked
in `recv` for client A while B waits). Fixing that — threads, then `epoll` — is
Week 2, and it's literally how nginx and Node work.
