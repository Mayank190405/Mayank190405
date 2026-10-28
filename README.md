<p align="center">
  <img src="./assets/hero-banner.svg" alt="Mayank Bajaj - System Architect & GenAI Developer" width="100%" />
</p>

<p align="center">
  <a href="https://mayank190405.github.io/visualizer/"><img src="https://img.shields.io/badge/⚡%20Algorithm%20Visualizer-Selection%20Sort%20Engine-D97757?style=for-the-badge&logoColor=white" alt="Algorithm Visualizer"></a>
  <a href="mailto:mayankbajaj773@gmail.com"><img src="https://img.shields.io/badge/Contact-Direct%20Dispatch-2B2621?style=for-the-badge&logo=gmail&logoColor=D97757" alt="Email"></a>
  <a href="https://github.com/Mayank190405"><img src="https://img.shields.io/badge/GitHub-@Mayank190405-2B2621?style=for-the-badge&logo=github&logoColor=FAF6EE" alt="GitHub"></a>
  <img src="https://img.shields.io/badge/Location-Nashik%20(UTC+5:30)-2B2621?style=for-the-badge&logoColor=D97757" alt="Location">
</p>

---

### ⚡ Interactive Algorithm Engine // Selection Sort Trace

> **Array Selection Invariant:** For each pass `i` from `0` to `n-1`, find the minimum element in unsorted sub-array `A[i..n-1]` and swap it into its final sorted position `A[i]`.

<p align="center">
  <a href="https://mayank190405.github.io/visualizer/">
    <img src="./assets/sorting-visualizer.svg" alt="Selection Sort Algorithm Visualizer" width="100%" />
  </a>
</p>

<p align="center">
  <a href="https://mayank190405.github.io/visualizer/">
    <strong>▶ [LAUNCH INTERACTIVE VISUALIZER: INPUT YOUR OWN NUMBERS & SORT]</strong>
  </a>
  <br>
  <sub>Features custom array entry, step-by-step pointers, Web Audio frequency synthesis, and live metric tracking.</sub>
</p>

```python
def selection_sort(arr: list[int]) -> list[int]:
    """Selects and sorts minimum elements in-place: O(n²) time, O(1) space."""
    n = len(arr)
    for i in range(n - 1):
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        if min_idx != i:
            arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr
```

---

### 🏛️ Production Architecture & System Topology

Every system I build is planned around four fault-isolated tiers: **Edge Ingress**, **Asynchronous Compute**, **Reasoning & RAG Retrieval**, and **Stateful Persistence**.

<p align="center">
  <img src="./assets/system-architecture.svg" alt="Production Architecture Specification" width="100%" />
</p>

#### Planned Architectural Decisions & Trade-Offs

```mermaid
flowchart TD
    subgraph Zone1 ["ZONE 01: EDGE & INGRESS (Stateless)"]
        A["Client Traffic\n(React / Next.js)"] -->|"HTTPS / WSS"| B["Reverse Proxy & TLS 1.3\nToken-Bucket Rate Limiter"]
        B -->|"JWT & RBAC Verified"| C["API Gateway Dispatch\n(P99 < 6ms)"]
    end

    subgraph Zone2 ["ZONE 02: ASYNC COMPUTE & WORKERS"]
        C -->|"HTTP/2"| D["FastAPI / Express Microservices\n(AsyncIO Event Loop)"]
        D -->|"Heavy Task Dispatch"| E["Celery / Redis Stream Queue\n(Worker Pool + DLQ)"]
    end

    subgraph Zone3 ["ZONE 03: INTELLIGENCE & HYBRID RAG"]
        D -->|"Prompt Intent"| F{"Autonomous Agent Core\nContext Window Optimizer"}
        F -->|"Dense Cosine (1536d)"| G["pgvector Store"]
        F -->|"Sparse Keyword Index"| H["BM25 Lexical Match"]
        G & H -->|"Reciprocal Rank Fusion"| I["Re-Ranker (98.4% Precision)"]
    end

    subgraph Zone4 ["ZONE 04: PERSISTENCE & CACHE"]
        D -->|"Sub-2ms Cache-Aside"| J[("Redis Cache Cluster\nPub/Sub & Distributed Locks")]
        D & F -->|"ACID Transaction Store"| K[("PostgreSQL\nWAL Replication")]
        D -->|"Dynamic CRM Payloads"| L[("MongoDB\nAggregated Audit Trails")]
    end

    classDef primaryNode fill:#241E1A,stroke:#D97757,stroke-width:2px,color:#FAF6EE;
    classDef secondaryNode fill:#1B1816,stroke:#3D352D,stroke-width:1.5px,color:#C2BCB2;
    classDef accentNode fill:#2E1B15,stroke:#E5A96A,stroke-width:1.5px,color:#FAF6EE;

    class F,I primaryNode;
    class A,B,C,D,E,J,K,L secondaryNode;
    class G,H accentNode;
```

#### 📐 Core Engineering Principles

* **1. Asynchronous Task Decoupling**: CPU-heavy LLM token processing and context embedding generation are isolated behind Redis stream worker queues with Dead Letter Queues (DLQ), ensuring public HTTP REST endpoints maintain a sub-20ms responsiveness under load.
* **2. Hybrid RAG (Dense + Sparse)**: Relying solely on vector embeddings leads to semantic hallucinations for domain-specific CRM keywords and IDs. The pipeline combines dense cosine similarity (pgvector) with sparse lexical search (BM25) fused via Reciprocal Rank Fusion (RRF).
* **3. Layered Cache-Aside**: Redis sits immediately upstream of PostgreSQL, handling session tokens, rate counters, and high-frequency queries to absorb over 80% of database read pressure.
* **4. Circuit Breakers & Graceful Degradation**: External AI API dependencies use automated circuit breakers with exponential backoff and localized fallback heuristics to prevent service-wide cascading failures.

---

### ⚡ Engineered Stack & Technical Matrix

A breakdown of technical proficiencies and system specializations:

<p align="center">
  <img src="./assets/tech-matrix.svg" alt="Engineered Stack Matrix" width="100%" />
</p>

---

### 📂 Featured Systems & Repositories

<table width="100%">
  <tr>
    <td width="50%" valign="top">
      <h4><a href="https://github.com/Mayank190405/bookmyveg-backend">📦 bookmyveg-backend</a></h4>
      <p>High-throughput backend engine for an on-demand agricultural supply-chain and grocery delivery platform.</p>
      <p>
        <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white"/>
        <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
        <img src="https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white"/>
        <img src="https://img.shields.io/badge/AsyncIO-D97757?style=flat-square&logoColor=white"/>
      </p>
      <ul>
        <li>Optimized asynchronous order queuing with transaction safety</li>
        <li>Dynamic geospatial store location matching algorithms</li>
      </ul>
    </td>
    <td width="50%" valign="top">
      <h4><a href="https://github.com/Mayank190405/jaydeveloperscrmbackend">🏢 jaydeveloperscrmbackend</a></h4>
      <p>Microservices infrastructure powering CRM workflows for real-estate developer teams and high-ticket customer lifecycles.</p>
      <p>
        <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white"/>
        <img src="https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white"/>
        <img src="https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white"/>
        <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white"/>
      </p>
      <ul>
        <li>Granular Role-Based Access Control (RBAC) & audit logging</li>
        <li>Automated webhook triggers for agent follow-ups and lead scoring</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h4><a href="https://github.com/Mayank190405/jd-crm">⚙️ jd-crm</a></h4>
      <p>Core workflow automation engine tailored for enterprise CRM pipeline tracking and lead qualification.</p>
      <p>
        <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
        <img src="https://img.shields.io/badge/CRM_Engine-D97757?style=flat-square&logoColor=white"/>
        <img src="https://img.shields.io/badge/REST_APIs-2B2621?style=flat-square&logoColor=white"/>
      </p>
      <ul>
        <li>Complex stage migration rules with zero data inconsistency</li>
        <li>Custom business analytics aggregation pipelines</li>
      </ul>
    </td>
    <td width="50%" valign="top">
      <h4><a href="https://github.com/Mayank190405/jd_frontend">💻 jd_frontend</a></h4>
      <p>Responsive, real-time administrative interface and CRM control room.</p>
      <p>
        <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black"/>
        <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black"/>
        <img src="https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white"/>
      </p>
      <ul>
        <li>Real-time dashboard telemetry and interactive Kanban pipelines</li>
        <li>Optimized component rendering with virtualized tables</li>
      </ul>
    </td>
  </tr>
</table>

---

### 📬 Dispatch & Collaboration

<p align="center">
  <a href="mailto:mayankbajaj773@gmail.com">
    <img src="./assets/footer-signature.svg" alt="Initiate Connection" width="100%" />
  </a>
</p>
