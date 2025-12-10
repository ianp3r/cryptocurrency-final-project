## Oracles in DLCs: Function, Limitations, and Dilemmas

### 1. What Is an Oracle in the Context of DLCs?

In the context of **Discreet Log Contracts (DLCs)**, an **oracle** is an entity that publishes cryptographic signatures about real-world events. These signatures allow Bitcoin financial contracts to be settled based on verifiable outcomes, such as asset prices, sports results, or economic indices.

To function as an oracle, an entity must:

- Predefine which events it will observe (e.g., the BTC/USD price at a specific time).
- Publicly commit to an **oracle public key** and to the set of **encoded possible outcomes**.
- Publish a **Schnorr signature** corresponding to the actual result once the event occurs.

Anyone can act as an oracle as long as they:

- Generate a valid key pair.
- Share their public key and message format.
- Ensure availability and authentication of signatures.

### 2. Limitations of the Oracle’s Power in DLCs

DLCs are designed to minimize the amount of trust required in the oracle, using cryptographic properties to restrict its power. Key characteristics include:

- **The oracle does not participate in negotiation nor knows the contract terms.**  
  It only publishes event data, unaware of who is using it.

- **The oracle does not control funds.**  
  All transactions are pre-signed by the parties before the result is revealed.

- **If the oracle lies or signs conflicting outcomes**, it exposes its private key, making it immediately accountable and losing all credibility.

- **Contract privacy:**  
  External observers cannot identify which events the contract references or what outcomes were anticipated, reducing manipulation risks.

These features create a system in which the oracle is essential but has minimal direct influence over contracts.

### 3. Oracle Dilemmas

Despite its cryptographic protections, the oracle model introduces dilemmas:

| Dilemma | Description |
|--------|-------------|
| **Trust centralization** | If few oracles dominate the market, the system becomes vulnerable to failures and coercion. |
| **Outcome manipulability** | Financial events may be influenced by actors with adverse incentives, creating conflicts of interest. |
| **Availability and censorship** | If the oracle fails to publish the result, settlements may be delayed or require fallback arbitration. |
| **Security risks** | A compromised private key undermines trust for all contracts depending on that oracle. |
| **Regulatory and legal pressure** | Oracles may become legal targets for providing data that moves large financial values. |

In summary, the oracle is the critical component connecting real-world events to Bitcoin via DLCs, but its existence introduces new risks and coordination challenges. DLC architecture significantly reduces the oracle’s power and trust requirements, yet it cannot completely eliminate the dilemmas associated with serving as an external source of truth.

## 4. Modern Solutions to the Oracle Problem

The pervasive integration of blockchain technology into various fields necessitates a corresponding focus on achieving enterprise-level mass adoption, a goal fundamentally dependent on the capabilities of smart contracts. This realization has catalyzed widespread academic and industrial research efforts directed at resolving the so-called *oracle problem*—a critical challenge to the utility of self-executing contracts. The ensuing work provides a systematic review of some of the existing literature on the oracle problem, concentrating specifically on the identification and assessment of potential mitigation strategies and solutions.

Between the proposed solutions, a large number were associated with limitations that may hinder their widespread adoption. For this reason, this work focuses on a **recent approach** to the problem: the role of **Artificial Intelligence (AI)** in tackling oracle reliability. The work developed by Giulio Caldarelli (ref number) emphasizes that AI should be understood as a **complementary layer of inference and filtering** within oracle design—**not** a substitute for trust assumptions.

> *“As blockchain applications continue to grow in complexity and criticality, ensuring the reliability, accuracy, and responsiveness of oracles becomes increasingly vital. Artificial Intelligence (AI) offers a broad spectrum of techniques that can enhance oracle systems across multiple dimensions, from anomaly and adversarial behavior detection to intelligent node selection, automated fact extraction, and the integration of hybrid AI-governance models. This section examines the various roles AI can play in enhancing oracle functionality, analyzing recent academic and industry developments that aim to strengthen oracles against manipulation, inefficiency, and unreliability.”*

| Topic | Description | Techniques | Applications and References |
|-------|-------------|------------|------------------------------|
| **AI for Anomaly detection in oracle data** | Detection of unexpected deviations in oracle inputs (due to technical errors or market fluctuations) using AI to enhance data reliability and prevent smart contract malfunctions | Statistical filtering, isolation forests, LSTM autoencoders, Kalman filters, conformal prediction, unsupervised learning, graph-based models, and Boltzmann machines | Chainlink (median filtering), (Breidenbach et al., 2021) Band Protocol (LSTM), (Protocol, 2024) Park et al. (Park et al., 2023), Kalman + conformal (Boltzmann fusion), multi-asset correlation models (Ikeda et al., 2025) |
| **Detection of adversarial and manipulative behavior** | AI methods are used to detect deliberate attempts to manipulate oracle data (e.g., flash loans, Sybil attacks), enhancing oracle resilience against targeted exploits | Reinforcement learning, supervised learning, clustering, graph-based detection, LLM-based reasoning, and temporal and semantic correlation analysis | RL oracle (Abinivesh S., 2025), AiRaceLX (LLM detection), (Gao et al., 2025) Forta (flash loan patterns), (Levin, 2025) Sybil detection via clustering (Alm’Ani et al., 2023) |
| **AI for oracle node selection** | AI enhances dynamic selection of oracle nodes by scoring them in real-time based on reputation, accuracy, and reliability, reducing dependency on static configurations and mitigating selection bias | Bayesian reinforcement learning, deep reinforcement learning, trust scoring, sliding window analysis, clustering | BLOR (Taghavi et al., 2022), TCODRL (Zhang et al., 2025), ETORM (Wang et al., 2024) |
| **Hybrid AI-governance models for oracle reliability** | Combining AI-driven evaluation with decentralized governance and cryptoeconomic incentives improves oracle reliability by aligning automated decision-making with community oversight and financial accountability | Reinforcement learning, staking and slashing, reputation systems, human-in-the-loop escalation, DAO-based governance | Supra’s Threshold AI (Supra, 2025), API3 DAO governance (Benligiray et al., 2022), Augur (Peterson et al., 2015), Kleros arbitration (Lesage et al., 2019), Tellor (Tellor, 2020) |
| **AI-driven fact extraction and verification** | LLMs and NLP models retrieve, interpret, and verify facts from unstructured sources (e.g., news, filings) before committing data on-chain. Cross-verification, grounding in source documents, and transparency mechanisms aim to enhance trust and accuracy | Large Language Models, semantic similarity voting, reasoning traces, multi-agent deliberation, cryptographic proof aggregation (e.g., BLS signatures), benchmarking, and role-based agent scoring | Chainlink LLM oracle prototype (Cryptopolitan, 2024), Supra’s prediction market resolver (Chainwire, 2025), Oraichain’s “Modestus” content moderation oracle (OraichainLabs, 2024), C-LLM and SenteTruth (Xian et al., 2024), LLM-query relayer framework (Xu et al., 2023) |

The table above provides a granular overview of how AI is being strategically deployed to address critical vulnerabilities within blockchain oracle systems. Applications range from **Anomaly Detection**, using models such as LSTM autoencoders and statistical filtering to enhance data reliability, to the **Detection of Adversarial and Manipulative Behavior** through reinforcement learning and LLM-based reasoning to defend against attacks like Sybil and flash loans.

Additionally, AI strengthens governance through **dynamic oracle node selection** using Bayesian learning and trust scoring, moving beyond static trust assumptions. The table also highlights the emergence of **Hybrid AI-governance models**, which combine automated AI evaluation with cryptoeconomic mechanisms—such as staking and slashing—for decentralized decision-making. Moreover, LLMs and NLP techniques enhance **fact extraction and verification** from unstructured data, aiming to improve grounding and transparency before off-chain information is committed on-chain.

Although AI is recognized as a powerful tool that offers a wide spectrum of capabilities for mitigating the oracle problem, its implementation introduces **specific challenges and inherent risks** that require careful evaluation. Fundamentally, these challenges stem from transferring the known vulnerabilities of complex AI systems—such as non-determinism, adversarial susceptibility, and bias—into the decentralized and trust-minimized architecture of blockchain networks.

A number of issues arise:

| Core challenges | Underlying causes | Implications for oracles | Key references |
|-----------------|-------------------|---------------------------|----------------|
| AI models are inherently imperfect; they can hallucinate, misclassify, or underperform in new contexts | High volatility in DeFi markets increases the difficulty of precise anomaly detection | False alerts or missed threats may lead to smart contract failures | Chandola et al. (2009), Gama et al. (2014), Goodfellow et al. (2016), Kilkenny and Robinson (2018), López de Prado (2018), OpenAI et al. (2024), Supra (2025) |
| They are vulnerable to false positives/negatives, data drift, hallucinations, and biases from training data | LLMs may generate plausible but incorrect content (“hallucinations”) | Hallucinated facts could trigger erroneous on-chain actions | same as above |
| same as above | Models trained on narrow datasets may fail in new domains (data bias) | Biased or outdated models may misreport data in unfamiliar conditions | same as above |
| same as above | Over time, changing data patterns lead to model drift or degradation | Decentralized retraining and updating are difficult and slow | same as above |
| same as above | GIGO principle: AI output is only as good as the data input | Full trustlessness cannot be guaranteed, as data source trust is still needed | same as above |





