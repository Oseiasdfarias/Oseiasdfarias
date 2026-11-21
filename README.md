<div align="center">

<picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/banner-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/banner-light.svg?v=3"><img alt="Oséias Farias, Applied AI and MLOps Engineer. Reliable AI for physical systems." src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/banner-dark.svg?v=3" width="100%"></picture>

</div>

<br>

I build AI systems that keep physical systems running: they detect when something fails and help fix it, in production. I come from electrical engineering and industrial maintenance, so I care about the system around the model, not only the model.

**Machine Learning & AI Engineer (MLOps)** · Brazil · open to remote roles · [Portfolio](https://oseiasdfarias.github.io) · [CV (EN)](https://oseiasdfarias.github.io/Oseias_Farias_CV_EN.pdf) · [CV (PT)](https://oseiasdfarias.github.io/Oseias_Farias_CV_PT.pdf) · [LinkedIn](https://www.linkedin.com/in/oseiasfarias/)

<picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-highlights-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-highlights-light.svg?v=3"><img alt="Highlights" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-highlights-dark.svg?v=3" width="100%"></picture>

| **Top 5%** | **1st author** | **−76%** | **90.5%** |
|:--|:--|:--|:--|
| in Tractian's ML Engineering hiring process, up to the final stage | of a paper at CBA 2026, the Brazilian Automation Conference | LLM calls with the RAG case memory in the UFABC · AFOSR research | of fraud stopped by [realtime-fraud-detection](https://github.com/Oseiasdfarias/realtime-fraud-detection) (synthetic data) |

<picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-experience-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-experience-light.svg?v=3"><img alt="Experience" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-experience-dark.svg?v=3" width="100%"></picture>

- **AI Engineer & Researcher · UFABC** (Apr 2025 – present), in a project funded by the U.S. Air Force Office of Scientific Research (AFOSR): a supervisor where **LLM agents** (CrewAI) close the loop with a power converter behind a deterministic safety gate. I built the **RAG-style case memory** (PostgreSQL + pgvector), which retrieves similar faults and reuses validated recipes (−76% LLM calls), and the **Simulink plant** in software/hardware-in-the-loop with its fault detection (**unscented Kalman filter**, CUSUM). A journal paper on the architecture is in preparation.

<details>
<summary><b>UFABC supervisor architecture, end to end</b> (the parts I built have an orange border)</summary>

```mermaid
flowchart TB
  subgraph PLANT["1 · Plant: MATLAB / Simulink, SIL and HIL"]
    direction LR
    SIM["Buck converter model<br/>and controller"] <-->|ZeroMQ| FDI["Fault detection and isolation<br/>unscented Kalman filter, CUSUM<br/>Python port, numerical parity"]
    FDI <-->|ZeroMQ| GW["Plant gateway"]
  end

  subgraph BUS["2 · Messaging"]
    direction LR
    TC["Supervisor gateway<br/>SQLite and Redis"] --> EVT["Event detector<br/>fault event, pre and post windows"]
  end

  subgraph FLOW["3 · Supervisor: CrewAI Flow"]
    direction TB
    MEM(["Case memory check<br/>reuse · adapt · explore · full"])
    subgraph CREWS["LLM crews"]
      direction LR
      OBS["observation"] --> ANA["analysis"] --> DIA["diagnosis"] --> RD["recipe_design<br/>structured output"]
    end
    CR["case_review crew<br/>gray zone"]
    GATE["Deterministic safety gate<br/>gain design, robustness checks"]
    JUDGE["recipe_evaluation crew<br/>and deterministic judge"]
    MEM -->|miss| OBS
    MEM -.->|unsure| CR
    MEM -->|close case| GATE
    CR --> GATE
    RD --> GATE
  end

  DB[("4 · RAG case memory<br/>PostgreSQL and pgvector")]

  GW -->|MQTT: states and faults| TC
  EVT --> MEM
  GATE -->|MQTT: recipe, bumpless swap| GW
  GW -->|post-fault window| JUDGE
  JUDGE -->|retain verified case| DB
  DB -->|similar cases| MEM

  classDef mine stroke:#d4885a,stroke-width:3px
  class SIM,FDI,GW,MEM,CR,DB mine
```

With the memory on, a paired campaign used **76% fewer LLM calls** and delivered the recipe about 0.4 s sooner in plant time.
</details>

- **Founder & Lead Engineer · [Otensor](https://docs.otensor.com.br)** (Jun 2026 – present): an IoT automation platform that connects ESP32 and Raspberry Pi devices to a real-time dashboard and an event-driven automation engine on AWS.
- **Backend & AI Developer · Verzel** (Dec 2025 – Jun 2026): voice AI and multi-tenant integrations for Lunella, an AI agent platform (Java/Quarkus, Vue.js, GraphQL, AWS serverless).
- **Education:** M.Sc. in Electrical and Information Engineering at UFABC (expected 2027); M.Sc. in Applied Computing at UFPA (2025–2027); B.Sc. in Electrical Engineering at UFPA (2024).

<picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-projects-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-projects-light.svg?v=3"><img alt="Featured projects" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-projects-dark.svg?v=3" width="100%"></picture>

<p align="center">
<a href="https://github.com/Oseiasdfarias/realtime-fraud-detection"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-fraud-detection-dark.svg?v=4"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-fraud-detection-light.svg?v=4"><img alt="realtime-fraud-detection: event-driven fraud decisions in milliseconds" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-fraud-detection-dark.svg?v=4" width="49%"></picture></a>
<a href="https://github.com/Oseiasdfarias/rastro-agent"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-rastro-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-rastro-light.svg?v=3"><img alt="rastro: complaint-to-root-cause AI agent" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-rastro-dark.svg?v=3" width="49%"></picture></a>
<a href="https://github.com/Oseiasdfarias/youfy"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-youfy-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-youfy-light.svg?v=3"><img alt="youfy: MLOps lab built around music" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-youfy-dark.svg?v=3" width="49%"></picture></a>
<a href="https://github.com/Oseiasdfarias/oseias_desafio_elite_dev_ia"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-sdr-agent-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-sdr-agent-light.svg?v=3"><img alt="sdr-agent: LLM agent with function calling" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/card-sdr-agent-dark.svg?v=3" width="49%"></picture></a>
</p>

<picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-stack-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-stack-light.svg?v=3"><img alt="Tech stack" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-stack-dark.svg?v=3" width="100%"></picture>

**AI & ML**<br>
<img alt="Python" src="https://img.shields.io/badge/Python-141416?style=flat-square&logo=python&logoColor=d4885a&labelColor=141416"> <img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-141416?style=flat-square&logo=pytorch&logoColor=d4885a&labelColor=141416"> <img alt="TensorFlow" src="https://img.shields.io/badge/TensorFlow-141416?style=flat-square&logo=tensorflow&logoColor=d4885a&labelColor=141416"> <img alt="scikit-learn" src="https://img.shields.io/badge/scikit--learn-141416?style=flat-square&logo=scikitlearn&logoColor=d4885a&labelColor=141416"> <img alt="CrewAI" src="https://img.shields.io/badge/CrewAI-141416?style=flat-square&logo=crewai&logoColor=d4885a&labelColor=141416"> <img alt="LangChain" src="https://img.shields.io/badge/LangChain-141416?style=flat-square&logo=langchain&logoColor=d4885a&labelColor=141416"> <img alt="OpenAI API" src="https://img.shields.io/badge/OpenAI%20API-141416?style=flat-square&logo=openai&logoColor=d4885a&labelColor=141416"> <img alt="MLflow" src="https://img.shields.io/badge/MLflow-141416?style=flat-square&logo=mlflow&logoColor=d4885a&labelColor=141416"> <img alt="DVC" src="https://img.shields.io/badge/DVC-141416?style=flat-square&logo=dvc&logoColor=d4885a&labelColor=141416">

**Cloud & back end**<br>
<img alt="AWS" src="https://img.shields.io/badge/AWS-141416?style=flat-square&logo=amazonwebservices&logoColor=d4885a&labelColor=141416"> <img alt="AWS Lambda" src="https://img.shields.io/badge/AWS%20Lambda-141416?style=flat-square&logo=awslambda&logoColor=d4885a&labelColor=141416"> <img alt="Terraform" src="https://img.shields.io/badge/Terraform-141416?style=flat-square&logo=terraform&logoColor=d4885a&labelColor=141416"> <img alt="Docker" src="https://img.shields.io/badge/Docker-141416?style=flat-square&logo=docker&logoColor=d4885a&labelColor=141416"> <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-141416?style=flat-square&logo=fastapi&logoColor=d4885a&labelColor=141416"> <img alt="Quarkus" src="https://img.shields.io/badge/Quarkus-141416?style=flat-square&logo=quarkus&logoColor=d4885a&labelColor=141416"> <img alt="GraphQL" src="https://img.shields.io/badge/GraphQL-141416?style=flat-square&logo=graphql&logoColor=d4885a&labelColor=141416"> <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-141416?style=flat-square&logo=postgresql&logoColor=d4885a&labelColor=141416"> <img alt="Redis" src="https://img.shields.io/badge/Redis-141416?style=flat-square&logo=redis&logoColor=d4885a&labelColor=141416"> <img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub%20Actions-141416?style=flat-square&logo=githubactions&logoColor=d4885a&labelColor=141416">

**Physical systems**<br>
<img alt="MATLAB / Simulink" src="https://img.shields.io/badge/MATLAB%20/%20Simulink-141416?style=flat-square&logo=mathworks&logoColor=d4885a&labelColor=141416"> <img alt="ZeroMQ" src="https://img.shields.io/badge/ZeroMQ-141416?style=flat-square&logo=zeromq&logoColor=d4885a&labelColor=141416"> <img alt="Raspberry Pi" src="https://img.shields.io/badge/Raspberry%20Pi-141416?style=flat-square&logo=raspberrypi&logoColor=d4885a&labelColor=141416"> <img alt="Espressif ESP32" src="https://img.shields.io/badge/Espressif%20ESP32-141416?style=flat-square&logo=espressif&logoColor=d4885a&labelColor=141416"> <img alt="MQTT" src="https://img.shields.io/badge/MQTT-141416?style=flat-square&logo=mqtt&logoColor=d4885a&labelColor=141416">

<picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-research-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-research-light.svg?v=3"><img alt="Research and publications" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-research-dark.svg?v=3" width="100%"></picture>

- **Farias, O. D.**, Estrada Martínez, E., Lescano, J. C. O. S., Potts, A. S. *Supervisão Adaptativa de Conversor Buck por Sistema Multiagente com Ciclo Percepção-Raciocínio-Ação e Reconfiguração Autônoma de Controladores*. Brazilian Conference on Automation (CBA), 2026. **Presented.**
- **Farias, O. D.**, Teixeira, R. B. *FCS-MPC com ARX Adaptativo via RLS para Controle P-Q Robusto a Variações Paramétricas em Inversores Trifásicos Conectados à Rede*. Brazilian Conference on Automation (CBA), 2026. **Presented.**
- Cota, Y. O., **Farias, O. D.**, Teixeira, R. B., Bayma, R. S. *Explorando o potencial do Laboratório Virtual de Controle de Sistemas com VPython no ensino de Engenharia*. COBENGE, 2023.

<picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-teaching-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-teaching-light.svg?v=3"><img alt="Teaching and writing" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-teaching-dark.svg?v=3" width="100%"></picture>

- **Udemy:** 2 Python courses for beginners, 2,100+ students.
- **YouTube:** [@otensor](https://youtube.com/@otensor), 1.7k subscribers.
- **Medium:** a 16-article series on MLOps, model serving, RAG and AI observability ([@oseiasfarias](https://medium.com/@oseiasfarias)).

<picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-connect-dark.svg?v=3"><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-connect-light.svg?v=3"><img alt="Connect" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/develop/assets/section-connect-dark.svg?v=3" width="100%"></picture>

<p align="center">
<a href="https://oseiasdfarias.github.io"><img alt="Portfolio" src="https://img.shields.io/badge/Portfolio-141416?style=flat-square&logo=googlechrome&logoColor=d4885a&labelColor=141416"></a> <a href="https://www.linkedin.com/in/oseiasfarias/"><img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-141416?style=flat-square&logo=linkedin&logoColor=d4885a&labelColor=141416"></a> <a href="https://medium.com/@oseiasfarias"><img alt="Medium" src="https://img.shields.io/badge/Medium-141416?style=flat-square&logo=medium&logoColor=d4885a&labelColor=141416"></a> <a href="https://youtube.com/@otensor"><img alt="YouTube" src="https://img.shields.io/badge/YouTube-141416?style=flat-square&logo=youtube&logoColor=d4885a&labelColor=141416"></a> <a href="https://orcid.org/0009-0005-4960-0271"><img alt="ORCID" src="https://img.shields.io/badge/ORCID-141416?style=flat-square&logo=orcid&logoColor=d4885a&labelColor=141416"></a> <a href="mailto:oseias.dfarias@gmail.com"><img alt="Email" src="https://img.shields.io/badge/Email-141416?style=flat-square&logo=gmail&logoColor=d4885a&labelColor=141416"></a>
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/output/snake-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/output/snake-light.svg">
    <img alt="Contribution graph animation" src="https://raw.githubusercontent.com/Oseiasdfarias/Oseiasdfarias/output/snake-dark.svg">
  </picture>
</p>
