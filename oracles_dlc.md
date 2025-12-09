# Oracles in DLCs: Function, Limitations, and Dilemmas

## 1. What is an Oracle in the Context of DLCs

In the context of *Discreet Log Contracts* (DLCs), an **oracle** is an
entity that publishes cryptographic signatures about real-world events.
These signatures allow financial contracts on **Bitcoin** to be settled
based on verifiable outcomes, such as asset prices, sports results, or
economic indices.

To function as an oracle, an entity must:

-   **Pre-define** which events it will observe (e.g., the price of
    BTC/USD at a specific time).\
-   Publicly **commit** to an **oracle public key** and the possible
    **encoded outcomes**.\
-   Publish a **Schnorr signature** corresponding to the actual result
    when the event occurs.

Any individual or institution can act as an oracle, provided they:

-   Generate a valid key pair.\
-   Disclose their public key and message format.\
-   Ensure the **availability** and **authenticity** of the signatures.

------------------------------------------------------------------------

## 2. Limitations of the Oracle's Power in DLCs

The design of DLCs aims to minimize the need for trust in the oracle by
utilizing cryptographic properties to limit its power:

-   **The oracle does not participate in the negotiation or know the
    terms of the contract.**\
    It only publishes event data, without knowing who will use that
    information.

-   **The oracle does not control funds.**\
    Transactions are already pre-signed between the parties before the
    result is revealed.

-   **If the oracle lies or signs conflicting results**, it reveals its
    private key, and can be held accountable and immediately loses
    credibility.

-   **Contract Privacy:**\
    External observers cannot identify which events the contract uses or
    which results were predicted, reducing manipulation vectors.

These limitations create a system where the oracle's function is
**essential**, but its direct influence over the contracts is
**minimal**.

------------------------------------------------------------------------

## 3. Oracle Dilemmas

  -----------------------------------------------------------------------
  Dilemma                     Description
  --------------------------- -------------------------------------------
  **Centralization of Trust** If few oracles dominate the market, the
                              system becomes vulnerable to failures and
                              coercion.

  **Result Manipulability**   Financial events can be influenced by those
                              with adverse incentives, creating conflicts
                              of interest.

  **Availability and          If the oracle does not publish the result,
  Censorship**                contract settlement may be delayed or
                              require alternative arbitration.

  **Security Risks**          Compromising the private key can invalidate
                              confidence in all contracts dependent on
                              that oracle.

  **Regulatory and Legal      Oracles can become legal targets for
  Pressure**                  providing data that moves large financial
                              values.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 4. Modern solutions to the oracle problem

The pervasive integration of blockchain technology into various fields
necessitates a corresponding focus on achieving enterprise-level mass
adoption, a goal fundamentally dependent on the capabilities of smart
contracts. This realization has catalyzed widespread academic and
industrial research efforts directed at resolving the so-called oracle
problem---a critical challenge to the utility of self-executing
contracts. The ensuing work provides a systematic review of some extant
literature available on the oracle problem, concentrating specifically
on the identification and assessment of potential mitigation strategies
and solutions.

Between the proposed solutions, a large number of them were associated
with a number of limitations that might hinder their widespread use. For
this reason this work will focus on a recent approach to the problem. We
will discuss the role of artificial intelligence (AI) in tackling the
oracle problem. The work developed by Giulio Caldarelli (ref number),
emphasizes the idea that AI should be understood as a complementary
layer of inference and filtering within the design of oracles, not a
substitute for trust assumptions.

> "As blockchain applications continue to grow in complexity and
> criticality, ensuring the reliability, accuracy, and responsiveness of
> oracles becomes increasingly vital. Artificial Intelligence (AI)
> offers a broad spectrum of techniques that can enhance oracle systems
> across multiple dimensions, from anomaly and adversarial behavior
> detection to intelligent node selection, automated fact extraction,
> and the integration of hybrid AI-governance models. This section
> examines the various roles AI can play in enhancing oracle
> functionality, analyzing recent academic and industry developments
> that aim to strengthen oracles against manipulation, inefficiency, and
> unreliability."

------------------------------------------------------------------------

### AI-Enhanced Oracle Techniques

  -------------------------------------------------------------------------------------------
  Topic            Description        Techniques           Applications and References
  ---------------- ------------------ -------------------- ----------------------------------
  **AI for Anomaly Detection of       Statistical          Chainlink (median filtering),
  detection in     unexpected         filtering, isolation Breidenbach et al. (2021), Band
  oracle data**    deviations in      forests, LSTM        Protocol (LSTM), Park et
                   oracle inputs (due autoencoders, Kalman al. (2023), Kalman + conformal,
                   to technical       filters, conformal   Boltzmann fusion, multi-asset
                   errors or market   prediction,          correlation (Ikeda et al., 2024).
                   fluctuations)      unsupervised         
                   using AI to        learning,            
                   enhance data       graph-based models,  
                   reliability and    Boltzmann machines.  
                   prevent smart                           
                   contract                                
                   malfunctions.                           

  **Detection of   Detecting          Reinforcement        RL oracle (Abinivesh S, 2025),
  adversarial and  deliberate         learning, supervised AIracleX (LLM detection) (Gao et
  manipulative     attempts to        learning,            al., 2025), Forta (flash loan
  behavior**       manipulate oracle  clustering, graph    patterns), Sybil detection
                   data (e.g., flash  detection, LLM       (Almi'Ani et al., 2023).
                   loans, Sybil       reasoning, temporal  
                   attacks) to        and semantic         
                   enhance            correlation          
                   resilience.        analysis.            

  **AI for oracle  Dynamic selection  Bayesian             BLOR (Taghavi et al., 2022),
  node selection** of oracle nodes    reinforcement        TCODRL (Zhang et al., 2025), ETORM
                   based on real-time learning, deep       (Wang et al., 2024).
                   reputation,        reinforcement        
                   accuracy, and      learning, trust      
                   reliability,       scoring, sliding     
                   reducing static    window analysis,     
                   configuration      clustering.          
                   vulnerabilities.                        

  **Hybrid         Combining          Reinforcement        Supra's Threshold AI (2025), API3
  AI-governance    AI-driven          learning,            DAO governance, Augur, Kleros
  models for       evaluation with    staking/slashing,    arbitration, Tellor.
  oracle           decentralized      human-in-the-loop,   
  reliability**    governance and     DAO governance.      
                   cryptoeconomic                          
                   incentives.                             

  **AI-driven fact Using LLMs and NLP LLMs, semantic       Chainlink LLM oracle prototype
  extraction and   to retrieve,       similarity voting,   (2024), Supra (2025), Oraichain
  verification**   interpret, and     reasoning traces,    "Modetus" (2024), C-LLM,
                   verify facts from  multi-agent          SenteTruth, LLM-query relayer (Xu
                   unstructured       deliberation,        et al., 2023).
                   sources before     cryptographic proof  
                   committing data    aggregation,         
                   on-chain.          benchmarking.        
  -------------------------------------------------------------------------------------------

------------------------------------------------------------------------

## Core Challenges of Integrating AI into Oracles

  ------------------------------------------------------------------------------------
  Core challenges        Underlying causes     Implications for oracles Key references
  ---------------------- --------------------- ------------------------ --------------
  **AI models are        High volatility in    False alerts or missed   Chandola et
  inherently imperfect:  DeFi markets          threats may lead to      al. (2009),
  they can hallucinate,  increases the         smart contract failures. Gama et
  misclassify, or        difficulty of precise                          al. (2014),
  underperform in new    anomaly detection.                             Goodfellow et
  contexts.**                                                           al. (2016),
                                                                        Kilkenny and
                                                                        Robinson
                                                                        (2018), López
                                                                        de Prado
                                                                        (2018), OpenAI
                                                                        et al. (2024),
                                                                        Supra (2025).

  **AI models are        LLMs may generate     Hallucinated facts could Same
  inherently imperfect:  plausible but         trigger erroneous        references as
  they can hallucinate,  incorrect content     on-chain actions.        above.
  misclassify, or        ("hallucinations").                            
  underperform in new                                                   
  contexts.**                                                           

  **They are vulnerable  Models trained on     Biased or outdated       Same
  to false               narrow datasets may   models may misreport     references.
  positives/negatives,   fail in new domains;  data in unfamiliar       
  data drift,            bias persists.        conditions.              
  hallucinations, and                                                   
  biases from training                                                  
  data.**                                                               

  **They are vulnerable  Changing data         Decentralized retraining Same
  to false               patterns lead to      and updating are         references.
  positives/negatives,   model drift or        difficult and slow.      
  data drift,            degradation over                               
  hallucinations, and    time.                                          
  biases from training                                                  
  data.**                                                               

  **They are vulnerable  GIGO principle: AI    Full trustlessness       Same
  to false               output is only as     cannot be guaranteed, as references.
  positives/negatives,   good as the data      data source trust is     
  data drift,            input.                still needed.            
  hallucinations, and                                                   
  biases from training                                                  
  data.**                                                               
  ------------------------------------------------------------------------------------
