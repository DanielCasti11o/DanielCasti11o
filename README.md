# Daniel Castillo — `dacastil` @ 42

Systems programming student at **42**. Most of my work is low-level C/C++ on Linux:
process and memory management, concurrency, graphics without engines, and containerized infrastructure.
Currently studying for **AWS Cloud Practitioner** ([notes, ES](https://www.notion.so/danielcasti11o/AWS-Cloud-Practitioner-273fe243807880f9815ef45c75eb4f43)).

```
languages   C · C++98 · Python · Bash · JavaScript
systems     POSIX processes, pipes, signals, file descriptors, pthreads/mutexes
graphics    MiniLibX, raycasting, Bresenham, isometric projection
infra       Docker, Docker Compose, NGINX (TLS), MariaDB, PHP-FPM, Linux
tooling     Git, Make, GDB, Valgrind, Vim, VSCode
```

---

## Featured

### [ft_transcendence — DeployHub](https://github.com/TranscendenceFortyTwo/transcendence) · 42 final project · team of 5
Mini **PaaS**: connect a Git repo → clone → `docker build` → run container → stream logs/status over WebSockets.
Microservice architecture on Docker Compose with PostgreSQL/Prisma, Traefik + ModSecurity (OWASP CRS), Prometheus/Grafana/cAdvisor.

**My part — `auth-service`:** standalone Node.js / Express 5 service with Prisma on PostgreSQL.
Local registration/login with bcrypt hashing and JWT issued in `httpOnly` cookies; OAuth 2.0 authorization-code flow
for **Google, GitHub and 42 Intra**; auth module integrated into the main backend and wired into the Compose stack.

### [GeoSignal](https://github.com/GeoSignalNASA/GeoSignal) · NASA Space Apps Challenge 2026 · *Dancing with the SARs*
Post-wildfire debris-flow risk mapping from **NISAR L-band SAR** + DEM + rainfall. Case study: Calvos de Randín burn (Ourense, Sept 2026).
Reproducible Python pipeline (AOI stack extraction, change detection, slope, basin delineation, flow-path tracing, risk index) feeding a static interactive StoryMap.

**My part — `alerts/` module:** rain-alert engine in pure Python stdlib. Polls the Open-Meteo 3-day forecast over the burn scar,
evaluates tiered thresholds (20/40/80 mm·24h, 10/20/40 mm·h), and delivers per-subscriber HTML reports and alerts via SMTP (cron-driven, dry-run by default).
Subscriber store, CLI (`subscribe`, `check`, `run --send`…), `ThreadingHTTPServer` endpoint backing the StoryMap's alerts section, `unittest` suite.

### [OverZenith](https://github.com/OverZenithTeam/OverZenith) · NASA Space Apps Challenge 2025
Gamified web app for exploring NASA content from a simulated ISS Cupola. React + TypeScript + Tailwind, 3D Earth with `react-globe.gl`, XP/levels via React Context + `localStorage`.

**My part:** interactive globe layer (geo-pinned info points and their data), quiz modal and asteroid content, Cupola view switching, team modal.

---

## Projects

### Systems / Unix

| Project | Stack | Technical summary |
|---|---|---|
| [**minishell**](https://github.com/eltitoyisus/mini) | C | Bash-like shell: tokenizer/parser, `fork`/`execve` pipelines, `<` `>` `>>` `<<` redirections, heredoc, environment expansion, builtins, `SIGINT`/`SIGQUIT` handling per process context. Team project. |
| [**pipex**](https://github.com/DanielCasti11o/PIPEX_42) | C | Reproduces `< in cmd1 \| cmd2 > out` with `pipe`, `dup2`, `fork`, `execve` and `PATH` resolution; correct fd closing and child exit-status propagation. |
| [**philosophers**](https://github.com/DanielCasti11o/Philosophers_42) | C, pthreads | Dining philosophers: one thread per philosopher, one mutex per fork, even/odd start staggering to avoid deadlock, mutex-protected shared state and ms-precision death monitoring. |
| [**Inception**](https://github.com/DanielCasti11o/Inception) | Docker | NGINX (TLSv1.2/1.3 only) → WordPress + PHP-FPM → MariaDB, each in its own container built from custom Alpine Dockerfiles. Compose orchestration, bridge network, persistent volumes, Docker secrets for credentials. |
| [**NetPractice**](https://github.com/DanielCasti11o/Net_practice) | TCP/IP | Subnetting, CIDR masks, routing tables and gateway configuration across multi-network topologies. |

### Graphics

| Project | Stack | Technical summary |
|---|---|---|
| [**cub3D**](https://github.com/DanielCasti11o/cub3D) | C, MiniLibX | DDA raycasting engine. `.cub` map parser with closed-map validation, per-face wall textures, RGB floor/ceiling, doors, mouse look and minimap. **125/100**. With [angelurano](https://github.com/angelurano). |
| [**FdF**](https://github.com/DanielCasti11o/FDF-42) | C, MiniLibX | Wireframe renderer for heightmaps: isometric projection, Bresenham line rasterization, direct image-buffer pixel writes. |

### Algorithms / core library

| Project | Stack | Technical summary |
|---|---|---|
| [**push_swap**](https://github.com/DanielCasti11o/Push_Swap-42) | C | Sorts integers using two stacks and a restricted op set (`sa` `pb` `ra` `rrr`…), minimizing instruction count. Index normalization + K-sort (√n-sized chunks). |
| [**get_next_line**](https://github.com/DanielCasti11o/GNL) | C | Line reader over arbitrary fds with a static buffer, configurable `BUFFER_SIZE` and multi-fd support. |
| [**ft_printf**](https://github.com/DanielCasti11o/FT_PRINTF42) | C | `printf` reimplementation with variadic args (`va_list`): `cspdiuxX%`. |

### C++

[**CPP-Modules**](https://github.com/DanielCasti11o/CPP-Modules) — C++98, modules **00 → 09 completed**.

| Module | Topics |
|---|---|
| [00](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module00) | Namespaces, classes, member functions, iostreams |
| [01](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module01) | Heap vs stack allocation, references, pointers to members, file streams |
| [02](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module02) | Orthodox Canonical Form, operator overloading, fixed-point arithmetic |
| [03](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module03) | Inheritance, diamond problem, virtual inheritance |
| [04](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module04) | Subtype polymorphism, abstract classes, interfaces, deep copy |
| [05](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module05) | Exceptions, custom exception classes |
| [06](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module06) | `static_cast`, `reinterpret_cast`, `dynamic_cast`, serialization, scalar type detection |
| [07](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module07) | Function and class templates |
| [08](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module08) | STL containers, iterators, algorithms |
| [09](https://github.com/DanielCasti11o/CPP-Modules/tree/main/CPP_Module09) | STL in practice: Bitcoin exchange (CSV + `std::map`), RPN evaluator, Ford-Johnson merge-insertion sort |

---

## Activity

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcasti11o/danielcasti11o/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcasti11o/danielcasti11o/output/github-contribution-grid-snake.svg">
  <img alt="contribution graph" src="https://raw.githubusercontent.com/danielcasti11o/danielcasti11o/output/github-contribution-grid-snake.svg">
</picture>
