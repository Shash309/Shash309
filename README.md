<!-- ===========================================================
     SHASH309 · GITHUB PROFILE
     Everything below is hand-built. The banner and the terminal
     are custom SVGs in ./assets — no template, no generator.
     =========================================================== -->

<div align="center">

<a href="https://shashwat-sharma-dev.vercel.app/">
  <img src="assets/banner.svg" width="100%" alt="Shashwat Sharma — Applied AI, Systems and Full-Stack Engineer" />
</a>

<br/>

<a href="https://github.com/Shash309?tab=repositories">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=14&pause=1800&color=00E5A0&center=true&vCenter=true&width=620&lines=Bi-LSTM+%2B+Bahdanau+attention%2C+%2B16.1+BLEU+over+baseline;Postgres+SKIP+LOCKED+job+queues+that+never+double-claim;RAG+over+entire+codebases+%E2%80%94+Groq+with+Ollama+failover;Terraform+%2B+Ansible+%2B+Jenkins%2C+because+clicking+deploy+is+a+bug;Solidity+smart+contracts+settling+real+insurance+claims" alt="Rotating summary of recent engineering work" />
</a>

<br/><br/>

<a href="https://shashwat-sharma-dev.vercel.app/"><img src="https://img.shields.io/badge/PORTFOLIO-060a10?style=for-the-badge&logo=vercel&logoColor=00E5A0&labelColor=060a10" alt="Portfolio" /></a>
<a href="https://www.linkedin.com/in/shashwat-sharma-042950288"><img src="https://img.shields.io/badge/LINKEDIN-060a10?style=for-the-badge&logo=linkedin&logoColor=38BDF8&labelColor=060a10" alt="LinkedIn" /></a>
<a href="mailto:shashwatsharma309@gmail.com"><img src="https://img.shields.io/badge/EMAIL-060a10?style=for-the-badge&logo=gmail&logoColor=A78BFA&labelColor=060a10" alt="Email" /></a>

</div>

---

### `~/about`

I like the parts of engineering most people skip: why attention actually beats a plain seq2seq, why two workers must never claim the same row, why a deploy should be a consequence of a `git push` and not a ritual.

B.Tech CSE (AI & ML) at **SRM IST**, 2023–27 · CGPA 8.6 · currently **ML Engineer Intern at Tata Steel**.

So far that has meant training models on real factory data, writing the FastAPI services that serve them, provisioning the AWS boxes they run on, and occasionally putting a Solidity contract in the middle just to see whether it holds. I build end to end — raw data, feature engineering, training, API, interface, pipeline — because the interesting failures live in the seams between those layers.

No ML-is-the-future posting. Just repos you can clone and run.

---

### `~/shipped --production`

| Where | What | Result |
|---|---|---|
| **Tata Steel** · `Nov 2025 – present` | XGBoost quality classifier over 15K+ TMT bar samples | **+17% F1** vs. baseline |
| **Techboxai** · `May – Jul 2025` | Face unlock + liveness verification · React · FastAPI · OpenCV · MediaPipe | **+18% precision** vs. baseline |

---

### `~/now`

```console
➜ ~ ls -t ~/work | head -4

DevFlow/                   branch-aware CI/CD — Jenkins → Docker → AWS → CloudWatch
attention-translator/      seq2seq + Bahdanau attention, trained and benchmarked
vle7-app/                  containerised deploys, one experiment at a time
Distributed-Job-Scheduler/ heartbeat reaper + DLQ promotion under concurrent workers

➜ ~ cat exploring.md
  → distributed systems correctness: locking, idempotency, graceful drain
  → attention internals, and what actually transfers to bigger architectures
  → Kubernetes beyond a Minikube demo
  → LLM retrieval that stays cheap at repo scale (caching, chunking, token guards)
```

---

### `~/projects --featured`

<table>
<tr>
<td width="50%" valign="top">

#### [attention-translator](https://github.com/Shash309/attention-translator)
`Python` · `PyTorch` · `Bi-LSTM` · `Jupyter`

Neural machine translation EN→FR: Bi-LSTM encoder, **Bahdanau additive attention**, LSTM decoder, trained on Multi30k.

Benchmarked against two honest baselines — a 5,764-word rule-based dictionary (19.17 BLEU) and a plain seq2seq (40.65 BLEU). Attention reaches **56.76 BLEU** for only 0.3M extra parameters.

Ships attention heatmaps that show which English word each French word came from, including the adjective–noun swap in *red shirt → t-shirt rouge*. The write-up also explains the one-word-left offset instead of hiding it.

</td>
<td width="50%" valign="top">

#### [Distributed-Job-Scheduler](https://github.com/Shash309/Distributed-Job-Scheduler)
`TypeScript` · `Postgres` · `Redis` · `Prisma` · `Docker`

A Sidekiq/BullMQ-style scheduling platform built from first principles rather than from a library.

Atomic claiming via raw SQL `FOR UPDATE SKIP LOCKED`, so hundreds of concurrent workers never double-claim and never block each other. Queue-level concurrency limits enforced inside the same transaction.

Plus the unglamorous parts that make a queue real: exponential backoff with jitter, DLQ promotion, Redis heartbeats with a reaper for dead workers, `SIGTERM` drain, idempotency keys, and pre-aggregated stats for O(1) dashboard reads.

</td>
</tr>
<tr>
<td width="50%" valign="top">

#### [RepoMind](https://github.com/Shash309/RepoMind) · [live](https://repo-mind-delta.vercel.app)
`Next.js 14` · `TypeScript` · `RAG` · `Groq` · `SQLite`

Chat with, visualise and refactor an entire codebase. Clone a repo, index it semantically, then ask what actually depends on what.

**Hybrid inference:** Groq (Llama 3.3 70B) as primary, automatic **Ollama** failover when the cloud is down — the pipeline stays online. Embeddings via Cohere, persisted in SQLite so re-indexing doesn't re-bill you.

Act Mode goes further than Q&A: the model plans, locates and applies edits across files behind token-safety guards.

</td>
<td width="50%" valign="top">

#### [InsureX](https://github.com/Shash309/InsureX)
`Solidity 0.8` · `Hardhat` · `FastAPI` · `React` · `Groq`

Insurance has two failure modes: nobody understands their policy, and claims are settled by whoever feels like it.

So: Llama 3.1 reads any policy and extracts coverage, exclusions and trap clauses, grades it A–F, and does it in six Indian languages. Policies are minted as NFTs — immutable, and yours.

Claims settle through smart contracts and oracles instead of a reviewer's inbox. Side-by-side AI comparison across seven categories for two competing policies.

</td>
</tr>
</table>

#### [DevFlow](https://github.com/Shash309/DevFlow) &nbsp;·&nbsp; `Jenkins` `Terraform` `Ansible` `Docker` `AWS` `Prometheus` `Grafana`

A multi-environment CI/CD pipeline where **the branch you push to decides the environment** — no dropdowns, no drift.

```
git push → Jenkins → tests → docker build → branch detection → deploy → health check → CloudWatch
```

Infrastructure as code (Terraform), configuration as code (Ansible), pipeline as code (`Jenkinsfile`). Its sibling [devops-webapp](https://github.com/Shash309/devops-webapp) is deliberately honest about its own boundary: GitHub Actions builds, tests and pushes to GHCR, and the README explains exactly why a hosted runner cannot reach a local Minikube cluster instead of faking that step.

<sub>Also worth a look: **[CAPE](https://github.com/Shash309/Cognitive-Minor)** — career recommendation engine fusing MiniLM embeddings, TF-IDF and Random Forest with a Big Five psychometric module · **[FaceUnlockSystem](https://github.com/Shash309/FaceUnlockSystem__Spoof-proof)** — gesture-based liveness checks, React + FastAPI + OpenCV · **[NutriNion](https://github.com/Shash309/NutriNion)** — Django nutrition tracking.</sub>

---

### `~/stack`

<table>
<tr><td><b>Core</b></td><td>

[![Core languages](https://skillicons.dev/icons?i=python,typescript,js,java,c,cpp,solidity&theme=dark)](https://skillicons.dev)

</td></tr>
<tr><td><b>AI / ML</b></td><td>

[![AI and ML](https://skillicons.dev/icons?i=pytorch,tensorflow,sklearn,opencv&theme=dark)](https://skillicons.dev)
&nbsp;<code>XGBoost</code> <code>MediaPipe</code> <code>Librosa</code> <code>MiniLM</code> <code>MLflow</code>

</td></tr>
<tr><td><b>Backend</b></td><td>

[![Backend](https://skillicons.dev/icons?i=fastapi,flask,django,nodejs,express,prisma&theme=dark)](https://skillicons.dev)

</td></tr>
<tr><td><b>Frontend</b></td><td>

[![Frontend](https://skillicons.dev/icons?i=react,nextjs,tailwind,html,css&theme=dark)](https://skillicons.dev)

</td></tr>
<tr><td><b>Data</b></td><td>

[![Databases](https://skillicons.dev/icons?i=postgres,mongodb,redis,sqlite,mysql&theme=dark)](https://skillicons.dev)

</td></tr>
<tr><td><b>Infra</b></td><td>

[![Infrastructure](https://skillicons.dev/icons?i=docker,kubernetes,terraform,ansible,jenkins,aws,githubactions,grafana,git,linux&theme=dark)](https://skillicons.dev)

</td></tr>
</table>

---

### `~/terminal`

<div align="center">
  <img src="assets/terminal.svg" width="900" alt="Terminal session: whoami returns an engineer who would rather ship it than describe it; interests are applied ML, backend systems, distributed queues, DevOps and Web3; philosophy is build, break, instrument, learn, repeat." />
</div>

---

### `~/metrics`

<div align="center">

<img height="165" src="https://github-readme-stats.vercel.app/api?username=Shash309&show_icons=true&hide_border=true&include_all_commits=true&bg_color=060a10&title_color=00E5A0&icon_color=38BDF8&text_color=8FA8BD&ring_color=00E5A0" alt="Shash309's GitHub statistics: stars, commits, pull requests and issues" />
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Shash309&layout=compact&hide_border=true&langs_count=8&size_weight=0.5&count_weight=0.5&exclude_repo=InsureX,SUPPLY-CHAIN-AI,sb1-hahricyg&bg_color=060a10&title_color=00E5A0&text_color=8FA8BD" alt="Most used languages across Shash309's repositories, weighted by repository count as well as size" />

<br/>

<img width="98%" src="https://github-readme-activity-graph.vercel.app/graph?username=Shash309&bg_color=060a10&color=8FA8BD&line=00E5A0&point=38BDF8&area=true&area_color=00E5A0&hide_border=true&custom_title=Commit%20activity%20%E2%80%94%20last%2031%20days" alt="Graph of Shash309's commit activity over the last 31 days" />

<br/>

<img height="150" src="https://streak-stats.demolab.com?user=Shash309&hide_border=true&background=060a10&ring=00E5A0&fire=38BDF8&currStreakLabel=00E5A0&sideLabels=8FA8BD&dates=52708A&currStreakNum=E9F6FF&sideNums=E9F6FF&stroke=00E5A033" alt="Shash309's contribution streak" />

</div>

---

<div align="center">

### `~/connect`

**[Portfolio](https://shashwat-sharma-dev.vercel.app/)** &nbsp;·&nbsp; **[LinkedIn](https://www.linkedin.com/in/shashwat-sharma-042950288)** &nbsp;·&nbsp; **[shashwatsharma309@gmail.com](mailto:shashwatsharma309@gmail.com)**

<br/>

<sub>Open to internships, collaborations, and problems that look unreasonable at first glance.</sub>

<br/><br/>

<code>exit 0</code>

</div>

<!--
  You read the source. Respect.

  $ curl -s https://api.github.com/users/Shash309 | jq -r .bio
  > now updated to something I actually believe

  Everything in this README is traceable to a repo you can clone.
  No invented metrics. The BLEU numbers are in attention-translator/README.md.
  If you got this far, open an issue titled "skip locked" — I owe you a reply.
-->
