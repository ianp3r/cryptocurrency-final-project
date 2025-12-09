## Oráculos em DLCs: Função, Limitações e Dilemas

### 1. O que é um oráculo no contexto de DLCs

No contexto de *Discreet Log Contracts (DLCs), um **oráculo* é uma entidade que publica assinaturas criptográficas sobre eventos do mundo real. Essas assinaturas permitem que contratos financeiros em Bitcoin sejam liquidados com base em resultados verificáveis, como preços de ativos, resultados esportivos ou índices econômicos.

Para funcionar como oráculo, uma entidade deve:

- Definir previamente quais eventos observará (ex.: preço do BTC/USD em um horário).
- Comprometer-se publicamente com uma *chave pública de oráculo* e com os possíveis *resultados codificados*.
- Publicar uma *assinatura Schnorr* referente ao resultado real quando o evento ocorrer.

Qualquer indivíduo ou instituição pode atuar como oráculo desde que:
- Gere um par de chaves válido.
- Divulgue sua chave pública e formato de mensagens.
- Garanta disponibilidade e autenticação das assinaturas.

### 2. Limitações do poder do oráculo no DLC

O design dos DLCs busca minimizar a necessidade de confiança no oráculo, utilizando propriedades criptográficas para limitar seu poder. Entre as principais características:

- *O oráculo não participa da negociação nem conhece os termos do contrato.*  
  Ele apenas publica dados do evento, sem saber quem usará essas informações.

- *O oráculo não controla fundos.*  
  As transações já são pré-assinadas entre as partes antes da revelação do resultado.

- *Se o oráculo mentir ou assinar resultados conflitantes*, ele revela sua chave privada, podendo ser responsabilizado e perdendo credibilidade imediatamente.

- *Privacidade dos contratos*:  
  Observadores externos não conseguem identificar quais eventos o contrato usa ou que resultados foram previstos, reduzindo vetores de manipulação.

Essas limitações cria um sistema em que a função do oráculo é essencial, mas sua influência direta sobre os contratos é mínima.

### 3. Dilemas do oráculo

Apesar das proteções criptográficas, a existência de um oráculo cria dilemas:

| Dilema | Descrição |
|--------|-----------|
| *Centralização de confiança* | Se poucos oráculos dominam o mercado, o sistema torna-se vulnerável a falhas e coerção. |
| *Manipulabilidade do resultado* | Eventos financeiros podem ser influenciados por quem possui incentivos adversos, criando conflitos de interesse. |
| *Disponibilidade e censura* | Se o oráculo não publicar o resultado, contratos podem atrasar liquidação ou exigir arbitragem alternativa. |
| *Riscos de segurança* | Comprometimento da chave privada pode invalidar a confiança em todos os contratos que dependem daquele oráculo. |
| *Pressão regulatória e legal* | Oráculos podem tornar-se alvos legais por fornecerem dados que movimentam grandes valores financeiros. |

Em resumo, o oráculo é um componente crítico para que DLCs conectem eventos reais ao Bitcoin, mas sua existência traz novos riscos e pontos de coordenação. A arquitetura dos DLCs reduz significativamente o poder e a confiança necessária no oráculo, mas não elimina completamente os dilemas associados ao seu papel como fonte de verdade externa.

``` markdown
# Section. n - Modern solutions to the oracle problem

The pervasive integration of blockchain technology into various fields necessitates a corresponding focus on achieving enterprise-level mass adoption, a goal fundamentally dependent on the capabilities of smart contracts. This realization has catalyzed widespread academic and industrial research efforts directed at resolving the so-called oracle problem—a critical challenge to the utility of self-executing contracts. The ensuing work provides a systematic review of some extant literature available on the oracle problem, concentrating specifically on the identification and assessment of potential mitigation strategies and solutions.

Between the proposed solutions, a large number of them were associated with a number of limitations that might hinder their widespread use. For this reason this work will focus on a recent approach to the problem. We will discuss the role of artificial intelligence (AI) in tackling the oracle problem. The work developed by Giulio Caldarelli (ref number), emphasizes the idea that AI should be understood as a complementary layer of inference and filtering within the design of oracles, not a substitute for trust assumptions.

> “As blockchain applications continue to grow in complexity and criticality, ensuring the reliability, accuracy, and responsiveness of oracles becomes increasingly vital. Artificial Intelligence (AI) offers a broad spectrum of techniques that can enhance oracle systems across multiple dimensions, from anomaly and adversarial behavior detection to intelligent node selection, automated fact extraction, and the integration of hybrid AI-governance models. This section examines the various roles AI can play in enhancing oracle functionality, analyzing recent academic and industry developments that aim to strengthen oracles against manipulation, inefficiency, and unreliability.”

The table above offers a granular overview of how Artificial Intelligence (AI) is being strategically deployed to tackle critical vulnerabilities within blockchain oracle systems. The applications span from Anomaly Detection, using models like LSTM autoencoders and statistical filtering to enhance data reliability by flagging unexpected deviations, to the Detection of adversarial and manipulative behavior through techniques such as reinforcement learning and LLM-based reasoning to secure the system against attacks like Sybil and flash loans. Furthermore, AI contributes to robust governance by enabling dynamic oracle node selection via Bayesian learning and trust scoring, moving beyond static trust configurations. Crucially, the table highlights the emerging trend of Hybrid AI-governance models that combine automated AI evaluation with established cryptoeconomic incentives (staking and slashing) for decentralized decision-making, alongside the deployment of LLMs and NLP for fact extraction and verification from unstructured data, ultimately aiming to ground off-chain information with greater transparency and accuracy before it is committed to the blockchain.

| Topic | Description | Techniques | Applications and References |
| :--- | :--- | :--- | :--- |
| **AI for Anomaly detection in oracle data** | Detection of unexpected deviations in oracle inputs (due to technical errors or market fluctuations) using AI to enhance data reliability and prevent smart contract malfunctions. | Statistical filtering, isolation forests, LSTM autoencoders, Kalman filters, conformal prediction, unsupervised learning, graph-based models, and Boltzmann machines. | Chainlink (median filtering), Breidenbach et al. (2021) Band Protocol (LSTM), Protocol (2024) Park et al. (2023), Kalman + conformal, (Boltzmann fusion), multi-asset correlation models (Ikeda et al., 2024). |
| **Detection of adversarial and manipulative behavior** | AI methods are used to detect deliberate attempts to manipulate oracle data (e.g., flash loans, Sybil attacks), enhancing oracle resilience against targeted exploits. | Reinforcement learning, supervised learning, clustering, graph-based detection, LLM-based reasoning, and temporal and semantic correlation analysis. | RL oracle (Abinivesh S, 2025), AIracleX (LLM detection) (Gao et al., 2025) Forta (flash loan patterns), (Levin, 2025) Sybil detection via clustering (Almi’Ani et al., 2023). |
| **AI for oracle node selection** | AI enhances dynamic selection of oracle nodes by scoring them in real-time based on reputation, accuracy, and reliability, reducing dependency on static configurations and mitigating selection bias. | Bayesian reinforcement learning, deep reinforcement learning, trust scoring, sliding window analysis, clustering. | BLOR (Taghavi et al., 2022), TCODRL (Zhang et al., 2025), ETORM (Wang et al., 2024). |
| **Hybrid AI-governance models for oracle reliability** | Combining AI-driven evaluation with decentralized governance and cryptoeconomic incentives improves oracle reliability by aligning automated decision-making with community oversight and financial accountability. | Reinforcement learning, staking and slashing reputation systems, human-in-the-loop escalation, DAO-based governance. | Supra's Threshold AI (Supra, 2025), API3 DAO governance (Benligiray et al., 2022), Augur (Peterson et al., 2015), Kleros arbitration (Lesage et al., 2019), Tellor (Tellor, 2020). |
| **AI-driven fact extraction and verification** | LLMs and NLP models are used to autonomously retrieve, interpret, and verify facts from unstructured sources (e.g., news, filings) before committing data on-chain, Cross-verification, grounding in source documents, and transparency mechanisms aim to enhance trust and accuracy. | Large Language Models, semantic similarity voting, reasoning traces, multi-agent deliberation, cryptographic proof aggregation (e.g., BLS signatures), benchmarking, and role-based agent scoring. | Chainlink LLM oracle prototype (Cryptopolitan, 2024), Supra's prediction market resolver (Chainwire, 2025) Oraichain's "Modetus" content moderation oracle (Oraichainlabs, 2024), C-LLM and SenteTruth (Xian et al., 2024), LLM-query relayer framework (Xu et al., 2023). |

Although Artificial Intelligence (AI) is recognized as a resourceful and powerful tool that offers a wide spectrum of services applicable to mitigating the oracle problem, its potential implementation introduces specific enhancement points and inherent concerns that necessitate careful consideration. Fundamentally, these challenges are rooted in the transference of established vulnerabilities of complex AI models (such as non-determinism, adversarial manipulation, and bias) into the decentralized, trust-minimized framework of the blockchain.

There are a few issues related:

| Core challenges | Underlying causes | Implications for oracles | Key references |
| :--- | :--- | :--- | :--- |
| **AI models are inherently imperfect: they can hallucinate, misclassify, or underperform in new contexts.** | High volatility in DeFi markets increases the difficulty of precise anomaly detection. | False alerts or missed threats may lead to smart contract failures. | Chandola et al. (2009), Gama et al. (2014), Goodfellow et al. (2016), Kilkenny and Robinson (2018), López de Prado (2018), OpenAI et al. (2024), Supra (2025). |
| **AI models are inherently imperfect: they can hallucinate, misclassify, or underperform in new contexts.** | LLMs may generate plausible but incorrect content ("hallucinations"). | Hallucinated facts could trigger erroneous on-chain actions. | Chandola et al. (2009), Gama et al. (2014), Goodfellow et al. (2016), Kilkenny and Robinson (2018), López de Prado (2018), OpenAI et al. (2024), Supra (2025). |
| **They are vulnerable to false positives/negatives, data drift, hallucinations, and biases from training data.** | Models trained on narrow datasets may fail in new domains (data bias). | Biased or outdated models may misreport data in unfamiliar conditions. | Chandola et al. (2009), Gama et al. (2014), Goodfellow et al. (2016), Kilkenny and Robinson (2018), López de Prado (2018), OpenAI et al. (2024), Supra (2025). |
| **They are vulnerable to false positives/negatives, data drift, hallucinations, and biases from training data.** | Over time, changing data patterns lead to model drift or degradation. | Decentralized retraining and updating are difficult and slow. | Chandola et al. (2009), Gama et al. (2014), Goodfellow et al. (2016), Kilkenny and Robinson (2018), López de Prado (2018), OpenAI et al. (2024), Supra (2025). |
| **They are vulnerable to false positives/negatives, data drift, hallucinations, and biases from training data.** | GIGO principle: AI output is only as good as the data input. | Full trustlessness cannot be guaranteed, as data source trust is still needed. | Chandola et al. (2009), Gama et al. (2014), Goodfellow et al. (2016), Kilkenny and Robinson (2018), López de Prado (2018), OpenAI et al. (2024), Supra (2025). |

The Core challenges of integrating AI into blockchain oracles, highlights that the inherent imperfections of AI models themselves pose significant risks to decentralized networks. A primary issue is that AI models are inherently imperfect, meaning they can misclassify, underperform in novel contexts, or even "hallucinate". These flaws lead to potential implications for oracles, such as false alerts or missed threats that could cause smart contract failures, or hallucinated facts triggering erroneous on-chain actions. The table further emphasizes the models' vulnerability to issues like data drift, false positives/negatives, and biases from training data, stemming from underlying causes like high market volatility in DeFi, the use of narrow training datasets, or changing data patterns leading to model degradation. A critical implication is that the GIGO (Garbage In, Garbage Out) principle suggests AI output is only as reliable as its input, meaning full trustlessness cannot be guaranteed as dependence on the data source trust remains.

```