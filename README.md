# 🚀 Automated Generative AI Curriculum Website

This repository hosts a responsive, highly structural curriculum website for the **Generative AI Course (Chapters 1–12)**. Built with Bootstrap 5 and deployed automatically via modern Cloud CI/CD practices.

📌 **Live Website URL:** [https://github.io](https://github.io)

---

## 🎨 System Architecture & CI/CD Workflow

The website utilizes a fully automated, **zero-cost serverless architecture**. Every time a code update is pushed, GitHub Actions instantly handles the pipeline and safely deploys the content to GitHub Pages.

```mermaid
graph TD
    %% Style Definitions (Colors & Styles)
    classDef init stroke:#2a5298,stroke-width:2px,fill:#eef2f7,color:#1e3c72;
    classDef dev stroke:#f39c12,stroke-width:2px,fill:#fef9e7,color:#b7950b;
    classDef ci stroke:#9b59b6,stroke-width:2px,fill:#f5eef8,color:#6c3483;
    classDef cd stroke:#2ecc71,stroke-width:2px,fill:#e8f8f5,color:#117a65;
    classDef success stroke:#27ae60,stroke-width:3px,fill:#d4efdf,color:#196f3d;

    %% Phase Grouping
    subgraph Phase_1 [Setup & Initialization]
        A[Create Public Repository] --> B(Set Source: GitHub Actions)
    end

    subgraph Phase_2 [Development & Code Update]
        C[Modify Website Content] -->|Edit index.html| D[Commit & Push to Main Branch]
    end

    subgraph Phase_3 [CI/CD Automation Pipeline]
        E{Trigger Workflow} -->|Detect Git Push| F[Checkout Code & Virtual Env]
        F --> G[Upload Static Artifacts]
        G --> H[Deploy to GitHub Pages Server]
    end

    %% Node Connections
    B --> C
    D --> E
    H --> I[Website Live & Success 🎉]

    %% Apply Styles
    class A,B init;
    class C,D dev;
    class E,F,G,H ci;
    class I success;
```

### ⚙️ Workflow Phase Breakdown

#### 1. Setup & Initialization Phase (初始化配置)
* **Public Repository:** The project repository must remain **Public** to leverage the free tier of GitHub Pages.
* **Actions Publishing Source:** The deployment engine bypasses legacy branch workflows and uses direct **GitHub Actions OIDC** runner integration for better security and speed.

#### 2. Development & Code Update Phase (開發與上傳)
* **Code Maintenance:** Web assets (e.g., `index.html`, CSS, JS) are kept neatly in the root directory.
* **Instant Triggers:** Committing updates via Git or the web UI immediately dispatches a webhook to the automation runner.

#### 3. Continuous Integration & Deployment Phase (CI/CD 自動化加速)
* **Virtual Runner:** An ephemeral Linux environment (`ubuntu-latest`) spins up on demand.
* **Artifact Bundling:** The system checks out the latest code version, verifies structural validity, and packages it using `actions/upload-pages-artifact`.
* **Secured Delivery:** The bundled artifact is directly pushed into the edge nodes of GitHub's hosting cluster via `actions/deploy-pages`.

#### 4. Live Production Phase (網站正式發布)
* **Zero-Downtime Swap:** Old cache assets are safely swapped behind the scenes without breaking current sessions.
* **Global Access:** The website updates live globally across the content delivery network under your personal namespace.

---

## 📁 Repository Structure
```text
.
├── .github/
│   └── workflows/
│       └── static.yml     # The core CI/CD automation workflow file
├── index.html             # Main responsive curriculum syllabus homepage
└── README.md              # Documentation (This file)
```

---

## 🛠 Tech Stack Built-In
* **Hosting Platform:** GitHub Pages (100% Free Resources)
* **Automation Automation:** GitHub Actions CI/CD Pipeline
* **Frontend UI Framework:** HTML5, CSS3, Bootstrap 5 (Responsive Layout)
* **Icons Pack:** Bootstrap Icons
