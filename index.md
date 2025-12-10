## Oracles in DLCs: Function, Limitations, and Dilemmas

## 1. What is Bitcoins DLCs?

In the world of cryptocurrencies, smart contract are a type of agreement that is scripted into the blockchains of bitcoin, rather than a simple transaction between users, in a way that the contract automatically executes once certain conditions are met, without the need of any intermediate or trust between the two parties of the agreement, improving transparency and efficiency when it comes to agreements. There exists a lot of types of smart contracts such as Pay-to-Public-Key-Hash (P2PKH), Multi-Signatures (Multisig) and Hashed Time Lock Contract (HTLC), among all this kinds of smart contracts, there is the one that’ll be the focus of this project, the Discreet Log Contract (or DLCs).

The key component that differs the DLC from other smart contracts is the oracle, a third-party that helps to settle the contract and the payment after the agreement is made, but how can there be a third-party if it was said earlier that smart contracts do not have intermediaries? It all revolves around the fact that the oracle is not a participant in the exchange, but rather an outsider that brings news about the real world to Bitcoin’s data. The oracle is someone responsible for bringing real-world information to Bitcoin’s blockchains or, in other words, is just someone who is responsible for updating the blockchains about real-life events, not being directly involved in the contract and, therefore, not an intermediary in it. But why does real-life events matter in a Bitcoin transaction? 

Discreet Log Contracts are used when someone wants to make a transaction depending on some real-life outcome (especially used for betting) and that’s where the oracle enters. A DLC is made when two parties agree on some contract that depends on the outcome of something in the real world, let’s imagine a scenario where we have 2 people, Alice and Bob, both agree to bet in the outcome of some football game in a way that, if team 1 win, Alice will receive the money they bet, on the other hand, if team 2 wins, Bob will get the money, when the match ends, it is known that team 1 won the game, so the oracle will update the system with that information, revealing that Alice won the bet and will receive the money. This scenario shows the importance of the oracle being someone that neither person (Alice and Bob) knows, or else, he could update the blockchain with an information that is not the real one, but would benefit the party that he knows.

In the creation of a DLC, there are some important points: The first one is when an oracle announces an event, this happens when it signs a message containing the details of the event (when it’ll happen, what are the possible outcomes), after that, both parties agree on betting in one (or more) of the announcements of one or more oracles and establish a contract with attestation points (the outcomes each one bet on). Then, they put the amount bet in a 2-of-2 multi-signature wallet and sign it with their private keys, sending it to the blockchain, also signing 2 more transactions, the CETs (Contract Execution Transactions), spending from the output of the first one they made, each CET is locked by the attestation points they established in the contract and also need the signature of the oracle to be published. Later, when the event occurs, the oracle reveals the attestation secret corresponding to the outcome that happened, the winner then uses this secret to sign the transaction and publish it in the blockchain.

Although betting is the most common example of use of DLCs, these contracts can be used for several other objectives, such as insurance contracts, since oracle-based transactions help trust-minimized (or even trustless) systems.

## 2. Why DLC is not currently used?

Even though DLCs bring various benefits to privacy, security and efficiency of transactions, also allowing new types of agreements, it still isn’t as used as other smart contracts, but why is that?  

It’s mostly because of the lack of security that is still present in current DLCs, but what makes a DLC be considered secure?  

The DLC security standard is analyzed in two major points. The first one revolves around the bet security or, in other words, if it is possible to guarantee to both parties that, at the end of the protocol, the coins are going to be distributed according to the agreement that was made in the start of the “bet”. The other point is if the oracle can be held accountable if the agreement is not fairly executed for any of the parts because of a malicious oracle, besides that, it must be impossible to blame an oracle for something that they didn’t do. If both of those requirements are met, then a DLC can be considered secure.

Besides that, another point that explains this lack of security in this kind of contract is the great number of different known attacks that can be made on them. Common attacks include Oracle-on-Oracle rogue key attack (when a malicious oracle chooses their announcement nonce to cancel out an attestation point of another oracle, in a way that they can combine both events to produce the attestation secret by itself), Oracle Signature Forgery (when someone that hold powers over what an oracle is going to attest to gets them to attest to a combination of outcomes in a way that they can forge a Schnorr signature by using these attestations) and User-on-User rogue key attack (happens when a malicious user pick their public key to cancel out some oracle’s attestation so that they don’t need that attestation to claim the prize).  

As we can see, a great part of the insecurity revolves around the existence and participation of the oracle in the contracts, so it’s safe to say that we urgently need a way to make oracle’s participation more secure, so that DLC can be broadly adopted. But, for that, we need to first deeply understand what is the oracle and what power they actually hold in a contract. 

### 3. What Is an Oracle in the Context of DLCs?

In the context of **Discreet Log Contracts (DLCs)**, an **oracle** is an entity that publishes cryptographic signatures about real-world events. These signatures allow Bitcoin financial contracts to be settled based on verifiable outcomes, such as asset prices, sports results, or economic indices.

To function as an oracle, an entity must:

- Predefine which events it will observe (e.g., the BTC/USD price at a specific time).
- Publicly commit to an **oracle public key** and to the set of **encoded possible outcomes**.
- Publish a **Schnorr signature** corresponding to the actual result once the event occurs.

Anyone can act as an oracle as long as they:

- Generate a valid key pair.
- Share their public key and message format.
- Ensure availability and authentication of signatures.

### 4. Limitations of the Oracle’s Power in DLCs

DLCs are designed to minimize the amount of trust required in the oracle, using cryptographic properties to restrict its power. Key characteristics include:

- **The oracle does not participate in negotiation nor knows the contract terms.**  
  It only publishes event data, unaware of who is using it.

- **The oracle does not control funds.**  
  All transactions are pre-signed by the parties before the result is revealed.

- **If the oracle lies or signs conflicting outcomes**, it exposes its private key, making it immediately accountable and losing all credibility.

- **Contract privacy:**  
  External observers cannot identify which events the contract references or what outcomes were anticipated, reducing manipulation risks.

These features create a system in which the oracle is essential but has minimal direct influence over contracts.

### 5. Oracle Dilemmas

Despite its cryptographic protections, the oracle model introduces dilemmas:

| Dilemma | Description |
|--------|-------------|
| **Trust centralization** | If few oracles dominate the market, the system becomes vulnerable to failures and coercion. |
| **Outcome manipulability** | Financial events may be influenced by actors with adverse incentives, creating conflicts of interest. |
| **Availability and censorship** | If the oracle fails to publish the result, settlements may be delayed or require fallback arbitration. |
| **Security risks** | A compromised private key undermines trust for all contracts depending on that oracle. |
| **Regulatory and legal pressure** | Oracles may become legal targets for providing data that moves large financial values. |

In summary, the oracle is the critical component connecting real-world events to Bitcoin via DLCs, but its existence introduces new risks and coordination challenges. DLC architecture significantly reduces the oracle’s power and trust requirements, yet it cannot completely eliminate the dilemmas associated with serving as an external source of truth.

## 6. Modern Solutions to the Oracle Problem

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

Overview of AI enhanced Oracle systems: 

![Alt text](https://images-provider.frontiersin.org/api/ipx/w=410&f=webp/https://www.frontiersin.org/files/Articles/1682623/fbloc-08-1682623-HTML/image_m/fbloc-08-1682623-g001.jpg "Overview of AI use in Oracle")

## 7. Conclusion

The oracle problem remains one of the most significant barriers to the widespread adoption of blockchain technology, as smart contracts fundamentally rely on accurate and trustworthy external data to function correctly. Despite considerable progress in both academic and industry-led initiatives, no single solution has fully resolved the tension between trust minimization, data reliability, and adversarial resilience. Recent developments, however, point toward the growing relevance of Artificial Intelligence (AI) as a complementary layer within oracle architectures rather than a replacement for existing trust assumptions.

AI-driven techniques—ranging from anomaly detection and adversarial behavior monitoring to intelligent node selection and automated fact verification—demonstrate promising capabilities in enhancing the robustness and responsiveness of oracle systems. These methods introduce adaptive, data-driven mechanisms capable of identifying subtle irregularities, mitigating manipulative attacks, and improving the overall quality of external inputs fed into smart contracts. Furthermore, emerging hybrid governance models suggest a future in which AI augments decentralized decision-making through transparent scoring, staking incentives, and human-in-the-loop validation.

Nevertheless, integrating AI into blockchain oracles introduces its own set of challenges. The inherent limitations of contemporary AI systems—including non-determinism, bias, vulnerability to data drift, and hallucinations—risk transferring well-known AI weaknesses into trust-minimized environments. This underscores the reality that AI-enhanced oracles cannot eliminate trust entirely; they instead redistribute and refine it. Ensuring the reliability of AI-supported systems requires continuous monitoring, rigorous model evaluation, and careful handling of data sources.

In summary, AI offers one of the most compelling and flexible avenues for addressing key aspects of the oracle problem, but it is not a panacea. The path forward will require a synthesis of cryptoeconomic incentives, distributed governance, robust data engineering, and responsible AI deployment. By embracing AI as a strategic enhancement rather than a total solution, the blockchain ecosystem can move closer to achieving the reliability and scalability necessary for true mass adoption.

## References

1. Bonnetain, X., & Neven, G. (2015). *Solving Discrete Logarithm Problems in Generic Groups*. IACR Cryptology ePrint Archive. Retrieved from https://eprint.iacr.org/2015/261.pdf

2. Trust Machines. *Discreet Log Contracts (DLCs): A Deep Dive*. Retrieved from https://trustmachines.co/learn/discreet-log-contracts-dlcs/

3. Bitcoin Magazine. (2023). *DLCs Are Evolving to Meet Institutional Needs*. Retrieved from https://bitcoinmagazine.com/technical/dlcs-evolving-to-meet-institutional-needs

4. Bitcoin Problems. *Secure Discreet Log Contracts*. Retrieved from https://bitcoinproblems.org/problems/secure-dlcs.html

5. Amenta, A., Rosen, D., Thibault, P., & Toledo, R. (2024). *Discreet Log Contracts*. Retrieved from https://static1.squarespace.com/static/6675a0d5fc9e317c60db9b37/t/66e4597b7f23866561a64a95/1726241147904/discreet+log+contracts+paper.pdf

6. ChainCatcher. *Research on Modern DLC Implementations*. Retrieved from https://www.chaincatcher.com/en/article/2119259

7. G. Malavolta, F. Zamyatin, et al. (2020). *Anonymous Multi-Hop Locks for Blockchain Scalability and Interoperability*. arXiv:2005.04377. Retrieved from https://arxiv.org/abs/2005.04377

8. A. Biryukov, D. Khovratovich, et al. (2023). *Advances in Adaptor Signatures and Their Applications to DLCs*. arXiv:2302.07911. Retrieved from https://arxiv.org/abs/2302.07911

9. NDSS Symposium (2023). *FALCON: Secure Oracle Designs for Blockchain Systems*. Retrieved from https://www.ndss-symposium.org/wp-content/uploads/2023/02/ndss2023_f24_paper.pdf

10. Caldarelli, G., et al. (2025). *AI-Assisted Oracle Models for Blockchain Security*. arXiv:2507.02125. Retrieved from https://arxiv.org/abs/2507.02125

11. Dryja, T. (2017). Discreet Log Contracts. MIT DCI. Retrieved from https://www.dci.mit.edu/s/discreet-log-contracts-paper.pdf

12. Alwen, J., Fuchsbauer, G., et al. (2023). Cryptographic Oracle-Based Conditional Payments. NDSS Symposium. Retrieved from https://www.ndss-symposium.org/wp-content/uploads/2023-24-paper.pdf

13. Zhang, R., Cecchetti, E., et al. (2023). From Reality Keys to Oraclize: A Deep Dive into the History of Bitcoin Oracles. arXiv:2302.07911. Retrieved from https://arxiv.org/abs/2302.07911

14. Zamyatin, A., et al. (2020). A First Look into DeFi Oracles. arXiv:2005.04377. Retrieved from https://arxiv.org/abs/2005.04377

15. Bitlayer Research Group. (2024). Analysis of DLC Principles and Optimization Thoughts. Retrieved from https://www.chaincatcher.com/en/article/2119259

16. Trust Machines. Discreet Log Contracts (DLCs): A Deep Dive. Retrieved from https://trustmachines.co/learn/discreet-log-contracts-dlcs/

17. Bitcoin Magazine. (2023). DLCs Are Evolving to Meet Institutional Needs. Retrieved from https://bitcoinmagazine.com/technical/dlcs-evolving-to-meet-institutional-needs

18. Bitcoin Problems. Secure Discreet Log Contracts. Retrieved from https://bitcoinproblems.org/problems/secure-dlcs.html

19. Kuwahara, I., et al. (2023). Off-Chain Discreet Log Contracts for Lightning Network Integration. Retrieved from https://cointhinktank.com/upload/offchaindlc.pdf

20. DLC Markets Research Group. (2024). A Non-Custodial Bitcoin Derivatives Trading System. Retrieved from https://dlcmarkets.com/whitepaper.pdf
