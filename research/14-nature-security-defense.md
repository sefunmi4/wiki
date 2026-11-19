# Nature, Security & Defense: A Survey of a Unified Research Programme

**Author:** Sefunmi Ashiru, Architecture of Homo Sapiens LLC
**Date:** November 2026 — Preprint (draft)

## Abstract

This paper surveys nature, security, and defense as a single research programme. It brings together five strands that are usually treated separately: nature-inspired defense engineering (biomimicry, bat echolocation, swarms, and immune-inspired security); acoustic defense and sonar; environmental and ecological security; and verification and trust in defense systems (provenance, attestation, and hash anchoring). The strands converge on three shared questions: resilience without a centre, sensing and verification under noise and deception, and nature as both model and stakes. The survey is grounded in cited sources — journal articles, conference papers, and institutional assessments — and grades the evidence by strand rather than blending it. Sources the author read in full are marked **verified live**; sources read only as search-result text are marked **index** and must be re-checked before final citation. A final section records concrete improvements the cited research suggests for the development of a software platform whose defense and security layer relies on signed commits, provenance and SBOMs, and blockchain-anchored publish receipts, labelling each transfer **Direct**, **Analogy**, or **Speculative**.

## 1. Introduction

Defense research has long borrowed from nature. Camouflage imitates animal coloration; sonar imitates bat echolocation; swarm tactics imitate flocking and schooling; intrusion detection imitates the immune system. At the same time, nature itself has become a security domain: climate change, resource scarcity, and ecosystem loss are now treated by NATO, the IPCC, and UNEP as security questions, not only environmental ones. And the systems that defend anything — a drone, a supply chain, a software release — must now *prove* what happened, through provenance, attestation, and tamper-evident records.

This paper treats those three facts as one programme rather than three fields. Section 2 covers nature-inspired defense engineering; Section 3 covers acoustic defense and sonar; Section 4 covers environmental and ecological security; Section 5 covers verification and trust; Section 6 states what a unified programme would study, its open questions, and where the fields disagree; Section 7 records implications for software development; Section 8 records limitations and what could not be verified.

Two cautions run throughout. First, no source was found that studies a unified "nature, security and defense" programme as such; the synthesis in Section 6 is the author's, built from the strand sources. Second, evidence quality is uneven across strands: Sections 3 and 5 rest on peer-reviewed, replicated results; Section 2 rests heavily on reviews, programme reports, and preprints; Section 4 rests on institutional assessments rather than experiments.

## 2. Nature-Inspired Defense and Security

### Key findings

**Minimal bat sonar works, at short range and low speed.** Bats navigate with one emitter and two receivers using broadband frequency-modulated (FM) pulses. Yamada et al. reproduced this with a 6.6 g thermophone plus two MEMS microphones (343 g total system), achieving about 17 mm ranging resolution by cross-correlation, and low-speed two-dimensional obstacle avoidance during autonomous flight even when microphone signals were dominated by rotor noise (about 94 dB SPL at 0.7 m) [1]. Verified live.

**Low-power ultrasound beats vision where vision fails, and fails where vision succeeds.** BatDeck (ETH Zurich) achieved ego-velocity mean squared error of 0.019 m/s and 8-minute / 136 m exploration among transparent and reflective obstacles, using sensors drawing under 1 mW. Its own comparison table shows cameras, laser time-of-flight, and ultrasound each fail differently, so robustness comes from complementing them, not replacing one with another [3]. Verified live.

**Bio-inspired materials are a parallel, more mature strand.** Nacre, mantis-shrimp dactyl clubs, cephalopod skin, and armadillo shells inspire armour, self-healing, energy dissipation, and adaptive camouflage; scalability, cost, and reliability under harsh conditions remain the stated bottlenecks [7][8]. Index sources.

**Mimicry is also concealment, deception, and imitation.** Matthews and Matthews (2024) trace military camouflage, deception with fakes and dummies, and imitation (animals, bioengineering, avian, insect, and mammal sonar) toward "robots, swarms, and avatars" driven by AI [6]. Index source.

**Swarm tactics have been demonstrated at scale by DARPA.** The OFFSET programme envisioned swarms of up to 250 collaborative autonomous air and ground systems for small units in urban areas, with a Swarm Tactics Exchange for composing collective behaviours, algorithms, and tactics [9]. Index source.

**Immune-inspired cybersecurity is a long literature with open scalability questions.** The human immune system is invoked for robust, self-organised, distributed protection; artificial immune systems (AIS) use negative and clonal selection, self/non-self discrimination, and immune memory for intrusion detection (notably the LISYS system). Reviews conclude substantial potential but call for work on scalability and on clonal selection and immune memory [10][11]. Index sources.

### Implications for development

**Complementary, fail-differently controls — Analogy, grounded in [3].** BatDeck's comparison shows no single sensor is robust; the system is robust because sensors fail differently. A software platform already has this shape (signed commits, SBOM, SAST/secret scanning, anchored receipts). The sourced improvement is to *test the combination for correlated failure*: a single compromised CI runner or a single signing key that defeats several checks at once is the equivalent of a sensor suite sharing one blind spot. Do not add a fifth check that shares the same trust root as the existing four.

**No single point of failure / quorum — Analogy, grounded in [9] and [12].** OFFSET's swarm has no central controller whose loss ends the mission; the Swarm-Mesh preprint proposes quorum thresholds so no single agent can trigger containment or be compromised undetected. Transferred to a platform: require more than one independent approval or signature for a publish (for example, author signature plus CI builder attestation), and make publish fail if either is missing. Speculative as a software claim: no source in this strand tests quorum approval for software releases.

**Self/non-self anomaly detection — Analogy, grounded in [10].** AIS distinguishes "self" from "non-self" and adapts. For a platform this supports an allowlist model already implicit in SBOMs: a release whose dependency set differs from the recorded SBOM should be treated as "non-self" and fail closed, rather than merely warned about. The AIS literature itself warns scalability is unresolved, so this should be a deterministic SBOM-diff check, not a learned anomaly detector, unless separately validated.

**Do not over-claim bio-inspiration.** A bio-inspired blockchain paper discussed in Section 5 claims 95.2% anomaly detection in simulation; that is a simulation claim, not a field result, and should not be cited as evidence a platform control works.

## 3. Acoustic Defense and Sonar

### Key findings

**Saranga (WPI, *Science Robotics* 2026) is the strongest result.** A 16 cm, roughly $400 palm-sized quadrotor using only 1.2 mW of sensing power and onboard computation navigated dense fog, darkness, and snow among thin and transparent obstacles, using a dual sonar array. It overcame a peak signal-to-noise ratio of −4.9 dB with two combined fixes: (a) a physical acoustic shield (inspired by bumblebee-bat ear cartilage) blocking propeller noise, and (b) a deep neural network denoising weak echoes using the long horizon of ultrasound echoes. Training generalised via a synthetic-data pipeline plus limited real noise data. Across 180 test flights success was 72–100%; it struggled with thin metal poles and slender branches that weakly reflect [2]. Verified live (arXiv abstract).

**Thermophone FM sonar (Yamada et al. 2026) shows the same noise problem solved differently:** broadband FM pulses plus cross-correlation pulse-compression gain plus thresholding, detecting a 12 cm pole while hovering under dominant rotor noise [1]. Verified live.

**Synthetic echolocation (Michigan, Army-funded) trains on simulation alone.** Patil et al. (2025, *Journal of Sound and Vibration* 119229) and Kwon et al. (2025, *IEEE Access*) trained ensembles of convolutional neural networks — each network for one shape — entirely on numerically simulated echoes, and classified real measured echoes, distinguishing spheres from cylinders despite similar curved frontal geometry; low-symmetry cubes head-on were the failure case. Funded by the US Army Research Office and DEVCOM Ground Vehicle Systems Center [4]. Index source (University of Michigan ARC project listing); the papers themselves were not opened.

**Hierarchical reinforcement learning is the WPI navigation stack.** The NSF-funded Sanket project (from September 2025, $704,908, 3 years) uses physics-informed deep learning to interpret ultrasound and a hierarchical reinforcement-learning stack to move toward goals while avoiding obstacles, fused with IMU and other sensors, for robots under 100 mm / 100 g, with real-world deployment aimed at 3–5 years [5]. Index source.

**Active noise cancellation for naval sonar: no strong peer-reviewed source was found.** Patent and trade material describes active cancellation (anti-phase counter-waves, reference hydrophones, adaptive algorithms) for hull, propeller, and torpedo-seeker noise, and acoustic cloaking and metamaterials as laboratory proof-of-concept with narrow bandwidth. This is a *gap*, not a finding — the patent analysis must not be cited as peer-reviewed evidence. The closest peer-reviewed analogue is Saranga's physical shield plus learned denoising, above.

### Implications for development

**Two-layer noise handling — Analogy, grounded in [2].** Saranga succeeds because it combines a *deterministic physical* fix (shield) with a *statistical* fix (learned denoising); neither alone sufficed at −4.9 dB SNR. For CI scanning, the analogue is: deterministic allowlists and baselines that suppress known-benign findings (the "shield") *plus* a second, independent check for what remains — not two copies of the same scanner. Speculative: no source tests this transfer to SAST/secret scanning; treat as a design hypothesis, not evidence.

**Synthetic-data testing of the verifier — Analogy, grounded in [2][4].** Both Saranga and the Michigan work generalise by training and testing on synthetic echoes plus limited real data. For a platform: generate synthetic tampered artifacts (mutated SBOM, re-signed commit, hash-mismatch receipt, swapped dependency) and require the verification path to catch them — that is, test the verifier, not just the happy path. This is a direct methodological transfer, but the *effectiveness* of synthetic testing for software verification is not established by these papers.

**Hierarchical checks (cheap local to expensive anchored) — Speculative, loosely grounded in [5].** WPI's hierarchical reinforcement learning does fast local avoidance before higher-level goal navigation. Analogously: run cheap local verification (recompute hash, check signature) on every publish, and reserve expensive anchored verification (on-chain receipt lookup, full SBOM diff) for releases and promotion gates. Flagged as speculative: the source does not discuss verification hierarchies.

**What this strand does *not* support:** active noise cancellation as a software pattern. Do not claim "active noise cancellation" as a sourced platform technique; the sourced techniques are physical shielding, cross-correlation and thresholding, and learned denoising.

## 4. Environmental and Ecological Security

### Key findings

**Climate change is a threat multiplier, not a direct cause of war — the consensus position.** IPCC AR6 WGII (2022) finds climate extremes are not directly causing new conflicts in large statistical studies; they prolong and increase the severity and frequency of ongoing violent conflicts, with a small but persistent signal, stronger where livelihoods depend on climate-sensitive agriculture and livestock and governance is weak. Higher warming increases conflict risk via food and livelihood insecurity [14][15]. Index sources.

**NATO has institutionalised this.** Its 2021 Climate Change and Security Action Plan calls climate change "one of the defining challenges of our times" and "a threat multiplier", and commits to four pillars: an annual Climate Change and Security Impact Assessment (awareness); adaptation into resilience, defence planning, capability delivery, standards, procurement, and training; mitigation via a greenhouse-gas-emissions mapping methodology for military activities; and outreach [16]. Verified live. NATO's topic page adds environmental security (extreme weather, sea-level rise, resource depletion, land degradation, pollution leading to humanitarian disasters, regional tensions, and violence), the Science for Peace and Security programme (since 1969), Trust Funds for demilitarisation and demining, and a Code of Conduct for active sonar to protect marine mammals, developed after CMRE research on sonar effects [17]. Verified live.

**Natural resources are central to conflict and to peacebuilding.** UNEP (2009): 40% of intrastate conflicts in the past 60 years were strongly linked to natural resources; such conflicts are twice as likely to relapse within five years; fewer than a quarter of peace agreements address natural-resource issues [18]. Index source. UNEP (2024), from 40 case studies, finds nature-based solutions (protect, conserve, restore, and sustainably use natural resources) are "uniquely placed to address underlying conflict drivers", while conflict itself directly threatens such projects, and inequality, economic incentives, and migration must be addressed [19]. Index source.

**Protection of nature is itself a security task.** NATO's sonar code of conduct is a concrete case of a defence capability being constrained to protect a natural system; UNEP's "Greening the Blue Helmets" work applies the same logic to peacekeeping's own environmental footprint [17][18].

### Implications for development

**Threat-multiplier risk framing — Analogy, grounded in [14][16].** IPCC and NATO insist a stressor rarely *causes* failure alone; it amplifies existing fragility. For a platform: treat a vulnerable dependency, a leaked secret, or an unsigned commit not as an isolated CVE to patch but as a multiplier on existing weaknesses (for example, a vulnerable crate matters far more if the same build can publish without a second signature). Prioritise fixes by *interaction* with existing fragility, not by severity score alone. Analogy, not a sourced software method.

**Annual / per-release impact assessment — Analogy, grounded in [16].** NATO conducts an *annual* Climate Change and Security Impact Assessment and integrates it into risk and resilience assessments and procurement. Analogously: a scheduled, recorded security-impact assessment per release (SBOM diff plus new dependencies plus changed attestations), stored alongside the anchored receipt, rather than ad-hoc review. This is a process transfer; no source tests it for software.

**Address underlying drivers, not only symptoms — Analogy, grounded in [19].** UNEP's lesson is that nature-based solutions work when they address underlying conflict drivers (inequality, incentives, livelihoods). For a platform: the analogue of "underlying drivers" is dependency hygiene and build hygiene (pinning, minimal dependencies, reproducible builds) rather than adding another scanner on top of an undisciplined supply chain. Speculative as a causal claim.

**Minimise collateral / data minimisation — Direct-ish, grounded in [17] and Section 5.** NATO constrained active sonar to protect marine mammals; the verification literature (Section 5) likewise holds that only a hash should leave the machine. For a platform: publish only digests and commitments, keep SBOMs and provenance evidence locally, and treat any collection of source or user data in a receipt as collateral to be avoided. This is supported by the anchoring sources in Section 5, not by the ecological sources alone.

## 5. Verification and Trust in Defense Systems

### Key findings

**SLSA gives the normative build-provenance ladder.** Specification v1.2, Build track: L1 provenance exists; L2 signed and authentic provenance from a hosted build service; L3 unforgeable provenance plus isolated and ephemeral builds. The producer must choose a capable platform, follow a consistent build, and distribute provenance. Provenance must identify the output by cryptographic digest. Critically: at L2 provenance *must* be generated by the control plane, not by a tenant or build step, and the signing key must be accessible only to the build service — not to user-defined build steps; at L3 every field is generated and verified in the trusted control plane, external parameters are fully enumerated, and cross-build and cache-poisoning influence is prohibited. Transparency logs or timestamping are recommended for key-compromise detection [20]. Verified live.

**Hash anchoring proves a narrow thing.** Committing a hash (or a Merkle root of many hashes) to a public chain proves the exact bytes existed at or before the block time and have not changed since; verification needs only the document, a small proof file, and public chain data. It does **not** prove authorship, accuracy, exclusivity (ten contradictory drafts can be anchored), legal execution, or precise time (hour-level for Bitcoin) [21]. Verified live. Haber and Stornetta (1991) hash-chaining predates blockchains; OpenTimestamps aggregates unbounded digests into one Bitcoin transaction, so individual timestamps are effectively free.

**The correct pattern is: anchor roots, keep proofs, verify on a schedule, combine instruments.** Filigrane's field notes: anchor Merkle roots not raw hashes (privacy amplification, batching); automate `.ots` proof upgrade after confirmation; store proofs with the documents; verify on a schedule (re-hash, walk the Merkle path, check the block header); plan for algorithm ageing (SHA-1 was retired); combine signature (origin) plus qualified TSA token (legal time) plus chain anchor (independent longevity) [21]. Verified live.

**A worked defence-supply-chain analogue exists (vendor white paper).** Sovereign Proof's Sentinel gives every serialized asset a signed, hash-chained custody biography (Ed25519, SHA-256, genesis value), a fleet Merkle root, and a single 32-byte commitment anchored to Bitcoin via OpenTimestamps, while all custody evidence stays inside the operator's facility. Its principles: determinism over judgment (an LLM narrates evidence, never computes a score); evidence stays home; tamper-evidence over tamper-prevention; fail closed (a missing attestation library is an error, never a silent downgrade to software); no token. Mutating a record breaks that record while the rest verifies; the fleet root then diverges from the anchor. Silicon binding uses TPM 2.0 quotes / DICE / SPDM over a challenge nonce; a quote from the wrong key is a fatal mismatch. It maps evidence to DFARS 252.246-7007/-7008 and NDAA FY2023 §5949 [22]. Verified live; vendor white paper, not peer-reviewed.

**Hardware attestation is the same pattern at the firmware layer.** NIST SP 800-193 (2018) organises platform firmware resiliency as Protection / Detection / Recovery. Secured boot only lets authenticated firmware execute, starting from a hardware root of trust; measured boot records hashes into TPM PCRs so a remote verifier can compare them to golden measurements (remote attestation) [23]. Index source (secondary summaries); the SLSA specification should be the primary citation for provenance.

**Sigstore / in-toto / Rekor complete the software stack.** Sigstore issues short-lived (about 10 minute) certificates bound to an OIDC identity (Fulcio), signs with Cosign, and logs every signing event in Rekor, an append-only Merkle transparency log. in-toto defines a *layout* (authorised steps, keys, and rules) plus signed *links* recording hashes of each step's inputs and outputs, so verification checks an unbroken signed chain from named source to artifact. SBOM formats are SPDX (ISO/IEC 5962) and CycloneDX (OWASP) [24]. Index, secondary sources; verify against sigstore.dev and in-toto.io before final use.

**Tamper-evidence is explicitly not tamper-prevention, and cannot defeat a fully compromised signer.** STAMP (molecular provenance preprint) states this plainly: it does not claim to defeat jailbroken synthesizers — that is irreducible — it is a cost imposer and evidence generator that converts attacks into forensically suspicious artifacts or supply-chain-visible events [25]. Index source; preprint, authors not captured.

### Implications for development — mostly Direct

These map onto a platform's existing controls (signed commits, verified author identity, provenance plus SBOMs, SAST/secret scanning, blockchain-anchored receipts) and are the most actionable part of this survey.

**Generate provenance in the control plane, not in the build — Direct, [20].** SLSA L2/L3 require the provenance generator to be the build platform itself, with the signing key inaccessible to user-defined build steps. *Improvement:* the platform's provenance and SBOM attestation must be emitted by the CI control plane (for example, GitHub Actions or the release service), never by application code or a build script that a compromised dependency could influence. If a build step can write its own provenance, the control is L1 at best.

**Aim explicitly at SLSA Build L2, then L3 — Direct, [20].** L2 is a hosted build plus signed provenance; L3 is isolated and ephemeral builds plus unforgeable provenance plus no cache-poisoning or cross-build influence. *Improvement:* state the target level in the platform's security documentation, and treat "builds on a developer laptop" and "shared, non-ephemeral runners with a persistent cache" as explicit L2/L3 failures.

**Anchor Merkle roots, not raw artifact hashes — Direct, [21][22].** Both Filigrane and Sovereign Proof anchor a single root (fleet or root commitment) rather than one transaction per document. *Improvement:* anchor one Merkle root per release covering the artifact hash plus SBOM hash plus provenance hash plus commit hash, and keep the per-artifact proof (Merkle path) with the release. This gives privacy amplification (an observer cannot count documents), negligible marginal cost, and a single batching point.

**Keep the proof, upgrade it, verify on a schedule — Direct, [21].** An OpenTimestamps-style receipt starts incomplete and must be upgraded after confirmation; a lost proof is a lost timestamp even though the anchor is permanent. *Improvement:* automate proof upgrade and retention with the artifact, and run scheduled re-verification (recompute hash, walk Merkle path, check block header) — evidence nobody has ever verified tends to fail the first time it matters [21].

**Do not let the receipt claim what it cannot prove — Direct, [21][25].** An anchor proves existence plus integrity at a coarse time only. It does not prove authorship, accuracy, exclusivity, or precise time. *Improvement:* the platform's "verified by recomputing the hash" check must be presented as existence and integrity only. Authorship needs the signed commit plus verified author identity (separate signature); uniqueness and sequence need an append-only log (cf. Rekor, [24]), not just an anchor; precise time needs an RFC 3161 TSA token if it matters. A false statement anchored on-chain is a false statement with a verifiable date [21].

**Fail closed, never silently downgrade — Direct, [22][23].** Sovereign Proof: a missing attestation library is an error, never a silent downgrade to software; a key that cannot decrypt the keystore refuses to mint keys. NIST SP 800-193: detection plus recovery, not just protection. *Improvement:* if signature verification, SBOM generation, or receipt verification is unavailable, the publish or deploy must fail — not proceed unsigned. Log the failure as a finding, not a warning.

**Deterministic scoring; evidence stays home — Direct, [22].** Trust must be computed by published, reproducible rules, never by a model's opinion; only a 32-byte commitment leaves the facility. *Improvement:* the platform's verification verdict should be a deterministic function of signatures plus hashes plus log inclusion (reproducible by any verifier from public data), and SBOM and provenance content should not be published on-chain — only its digest or root.

**Bind identity to silicon or key, with a challenge nonce — Direct, [22][23].** TPM quotes over a fresh nonce, verified against the key the device was born with. *Improvement (for the mobile and server components):* where a device or build runner holds a key, verify a fresh challenge and response at publish time rather than accepting a stored "I am authorised" claim; a quote from the wrong key is a fatal mismatch, not a warning.

**State honest limitations — Direct, [22][25].** Sovereign Proof and STAMP both publish a limitations section (hardware backends are roadmap, not shipped; jailbroken signers are irreducible). *Improvement:* the platform should document what its receipts do *not* defeat — for example, a compromised signing key, a compromised CI control plane, or a malicious authorised author — and what would make such an attack visible (transparency log, anchor divergence).

## 6. How the Strands Connect

### What a unified programme would study

The strands converge on three shared questions, each visible in the sources above.

**1. Resilience without a centre.** How do systems survive the loss of components? Bats navigate with a minimal sensor set; swarms (OFFSET) and quorum systems (Swarm-Mesh) survive node loss; immune systems are distributed and self-organised; SLSA, Rekor, and hash-anchoring survive the loss of any single vendor because verification needs only public data. The programme's core hypothesis — *redundancy plus local rules plus verifiable evidence beats a single hardened centre* — is the common thread, but it is a hypothesis, not a proven theorem across domains.

**2. Sensing and verification under noise and deception.** Ultrasound at −4.9 dB SNR, climate signals inside noisy conflict statistics, and tampered provenance inside a noisy supply chain are the same epistemic problem: extracting a trustworthy signal when the channel is degraded and the adversary may be active. Saranga's two-layer answer (deterministic shield plus statistical denoising) and SLSA's answer (control-plane provenance plus transparency log) are domain-specific instances of the same pattern.

**3. Nature as both model and stakes.** Nature supplies the design (echolocation, swarm, immunity) *and* is the thing being defended (marine mammals versus sonar, ecosystems versus climate-driven conflict, resources versus war). NATO's sonar code of conduct is the clearest institutional example of holding both roles at once.

### Open questions

- **What is the right level of bio-fidelity?** Yamada et al. note a "fundamental gap between biological and artificial airborne sonar" — bats adjust pulse intensity, time–frequency structure, and beam width dynamically; current drones do not, and fly at 0.4 m/s. Is closer imitation the path, or is the bat a proof that minimal architectures suffice?
- **Can immune and swarm ideas scale to real software systems?** AIS reviews (2007, 2025) still list scalability, clonal selection, and immune memory as open; the bio-inspired blockchain paper's 95.2% / 15.2 ms figures are simulation claims. No source in this survey demonstrates a fielded AIS or swarm-immune system at production scale.
- **Does anchoring scale as a social institution, not just a cryptographic one?** OpenTimestamps can anchor billions of hashes cheaply, but the Filigrane analysis shows the binding constraints are proof custody, algorithm ageing, legal standing (eIDAS qualified timestamps versus admissible-but-unprivileged anchors), and whether anyone actually verifies on a schedule.
- **Who decides when "nature-inspired" becomes "nature-militarised"?** See disagreements below.
- **Can ecological security be operationalised without securitising nature?** NATO's annual assessment and UNEP's nature-based solutions both assume institutions can measure and act; neither source resolves how to do so without turning ecosystems into military assets.

### Disagreements and gaps

**Climate determinism versus threat multiplier.** The IPCC/NATO consensus (threat multiplier, weak average effect at present) is contested by more deterministic readings in popular and some policy literature, and by a 2026 GMACCC paper framing climate change as "the primary threat to global peace and security" — a framing the IPCC's own assessment does not support in that strong form. A paper must not present determinism as the IPCC position.

**Militarised biomimicry.** Matthews and Matthews treat mimicry as continuous with deception and imitation in war; critical scholarship (for example, Foster and Clapper, "Swim, Swarm, Strike", conference paper [26]) argues biomimetic drones recast nature as a terrain of permanent counterinsurgency. This is a normative disagreement, not an empirical one, and a unified programme must address it rather than assume biomimicry is neutral.

**Tamper-evidence versus tamper-prevention.** SLSA, Sovereign Proof, and STAMP all insist tamper-evidence is not prevention; a system that presents anchored receipts as *preventing* tampering over-claims. The disagreement in the literature is about how much deterrence evidence actually provides when the attacker controls the signer.

**Evidence quality is uneven across strands.** Sections 3 and 5 have peer-reviewed, replicated results; Section 2's swarm and immune claims rest heavily on reviews, DARPA programme reports, and preprints; Section 4's strongest claims are institutional assessments, not experiments. A unified paper should grade evidence by strand, not blend them.

**Gaps found in this survey (not in the sources):** (a) no peer-reviewed source on active noise cancellation for sonar was located — only patent and trade material; (b) no source directly studies a unified "nature, security and defense" programme — the synthesis in this section is the author's, built from the strand sources; (c) no source was found that tests bio-inspired patterns (swarm, immune) as *software supply-chain* controls — all platform transfers in Sections 2–4 are analogies and are labelled as such.

## 7. Development Improvements at a Glance

| Strand | Strongest platform-relevant takeaway | Status |
|---|---|---|
| 1. Biomimicry | Complementary, fail-differently checks; no single point of failure; quorum / multi-party approval | Analogy, grounded in BatDeck + OFFSET |
| 2. Acoustic / sonar | Two-layer noise handling (deterministic shield + statistical denoising); synthetic-data testing of the verifier; hierarchical (cheap local → expensive anchored) checks | Analogy / Speculative |
| 3. Ecological security | Threat-multiplier risk framing; annual impact assessment; address root-cause drivers; minimise collateral / data minimisation | Analogy |
| 4. Verification | SLSA L2/L3 control-plane provenance; key must not be reachable by build steps; anchor Merkle roots, not raw hashes; verify on a schedule; fail closed; anchor does not prove authorship | **Direct** |
| 5. Connection | Deterministic, reproducible trust scoring; evidence stays home, only a 32-byte commitment leaves; tamper-evidence over tamper-prevention | **Direct** (Sovereign Proof pattern) |

"Direct" means the source states the pattern and it maps onto the platform's existing controls; "Analogy" means the pattern is in the source and the transfer to software is an inference; "Speculative" means a plausible transfer with no source support for the software application.

## 8. Limitations and What Could Not Be Verified

- **Active noise cancellation (sonar):** no peer-reviewed source located; only patent and trade summaries. Do not cite ANC as an established peer-reviewed sonar technique without further research.
- **Michigan echolocation paper details:** authors, volume and pages, and DOI for Patil et al. *Journal of Sound and Vibration* 119229 and Kwon et al. *IEEE Access* (2025) are taken from the University of Michigan ARC project listing (index); the papers themselves were not opened. Verify before final bibliography.
- **MDPI bio-inspired blockchain authors:** the abstract page as opened did not display author names in the extracted text; do not add authors without re-checking.
- **NIST SP 800-193 and Sigstore/in-toto specifics:** read via secondary summaries (index). The SLSA specification itself was verified live and should be the primary citation for provenance; Sigstore and Rekor details should be verified against sigstore.dev and in-toto.io before final use.
- **No source was found for a unified "nature, security and defense" programme as such.** Section 6's synthesis is an original synthesis from the strand sources, not a sourced claim.
- **Platform transfers in Sections 2–4 are analogies.** Only Section 5's improvements are directly stated by their sources. The labels must not be removed in the final paper.
- **STAMP authors and year:** not captured from the manuscript PDF as opened; cite by title only until verified.

## References

1. Yamada, Y., Hasegawa, K., Watabe, Y., Sasaki, S., Asada, T. & Hiryu, S. (2026). "A thermophone based FM sonar for airborne ultrasonic sensing under drone flight noise." *Scientific Reports* 16:26651. DOI: 10.1038/s41598-026-65909-3. https://www.nature.com/articles/s41598-026-65909-3.pdf — verified live.
2. Velmurugan, M., Brush, P., Balfour, C., Przybyla, R. J. & Sanket, N. J. (2026). "Milliwatt ultrasound for navigation in visually degraded environments on palm-sized aerial robots." *Science Robotics* 11(112), eadz9609. DOI: 10.1126/scirobotics.adz9609. https://arxiv.org/abs/2603.24699v1 — verified live (arXiv abstract).
3. Müller, H., Kartsch, V., Magno, M. & Benini, L. (2024). "BatDeck — Ultra Low-power Ultrasonic Ego-velocity Estimation and Obstacle Avoidance on Nano-drones." arXiv:2412.10048v1. https://arxiv.org/html/2412.10048v1 — verified live. Earlier version: arXiv:2403.16696v1.
4. Patil, G. U., Kwon, H. S., Epureanu, B. I. & Popa, B. I. (2025). "Synthetically-trained neural networks for shape classification from measured acoustic scattering." *Journal of Sound and Vibration*, 119229. Kwon, H. S., Patil, G. U., Epureanu, B. I. & Popa, B. I. (2025). "Specialized Convolutional Neural Network Models for Echolocation-Based Perception." *IEEE Access*. As listed at https://arc.engin.umich.edu/research/projects/perception-in-complex-scenes-using-automatically-labeled-sonar-imaging-data-in-synthetic-environments/ — index.
5. Worcester Polytechnic Institute / Sanket, N. J. NSF project on bat-inspired echolocation drones (2025–). Reported at https://i-hls.com/archives/132067 and https://fixedd.co.uk/bats-inspire-wpi-researchers-to-develop-drones-using-echolocation/ — index. Hierarchical reinforcement learning plus physics-informed deep learning; under 100 mm / 100 g.
6. Matthews, R. & Matthews, T. (2024). "Military mimicry: the art of concealment, deception, and imitation." *Defence and Security Analysis*. DOI: 10.1080/14751798.2024.2352271. https://research.birmingham.ac.uk/en/publications/military-mimicry-the-art-of-concealment-deception-and-imitation/ — index.
7. "Innovation of Bio-Inspired Materials for Next-Generation Defense Applications." (2025). IGI Global, ch. 5. DOI: 10.4018/979-8-3373-0933-0.ch005. https://www.igi-global.com/viewtitlesample.aspx?id=382059&ptid=361704&t=Innovation+of+Bio-Inspired+Materials+for+Next-Generation+Defense+Applications — index. Nacre, mantis shrimp, cephalopod camouflage, self-healing.
8. "Biomimetic design and impact simulation of Al2O3/Al composite armor based on armadillo shell." *Scientific Reports* (2024). https://www.nature.com/articles/s41598-024-71255-z — index. Armadillo carapace plus triply periodic minimal surfaces; simulation only, ballistic performance not yet experimentally proven for the TPMS variant.
9. DARPA (2020). "OFFSET Swarm Systems Integrators Demonstrate Tactics to Conduct Urban Raid." https://www.darpa.mil/news/2020/offset-swarm-urban-raid — index. 250-system swarms, urban raid field experiment, Camp Shelby.
10. Kim, J., Bentley, P. J., Aickelin, U., Greensmith, J., Tedesco, G. & Twycross, J. (2007). "Immune system approaches to intrusion detection — a review." *Natural Computing* 6:413–466. DOI: 10.1007/s11047-006-9026-4. https://staff.fmi.uvt.ro/~daniela.zaharie/ma2017/projects/applications/intrusion_detection_systems/AIS%2BIDS/AIS_intrusion_detection.pdf — index.
11. Bala, A. & El Bhiri, B. (2025). "A Comparative Analysis of Immunity-Inspired Cybersecurity Approaches." *Engineering Proceedings* 112, 73. DOI: 10.3390/engproc2025112073. https://mdpi-res.com/d_attachment/engproc/engproc-112-00073/article_deploy/engproc-112-00073.pdf?version=1764318708 — index.
12. Rolle, J. S. (2026). "Swarm-Mesh: A Decentralized Bio-Inspired System for AI Containment." Zenodo preprint, DOI: 10.5281/zenodo.21200799. https://zenodo.org/records/21200799/files/SwarmMesh_AI_Containment_Preprint_2026-07-04.pdf — index; independent preprint, not peer-reviewed. Quorum-sensing, resilient consensus, no single point of failure.
13. "Bioinspired Blockchain Framework for Secure and Scalable Wireless Sensor Network Integration in Fog–Cloud Ecosystems." (2024). *Sensors* / MDPI, 14(1):3. https://www.mdpi.com/2073-431X/14/1/3 — verified live (abstract). Authors not captured; do not cite author names. AIS plus Proof of Adaptive Immunity Consensus; claimed 95.2% anomaly detection, 500 nodes.
14. IPCC (2022). *Climate Change 2022: Impacts, Adaptation and Vulnerability.* Contribution of Working Group II to the Sixth Assessment Report. https://www.ipcc.ch/report/ar6/wg2/ — index (cited via secondary summaries).
15. New Security Beat. "What Next for Climate Security? Implications From IPCC Working Group II 6th Assessment Report." https://WWW.NEWSECURITYBEAT.ORG/?p=119047 — index. Also: *Climatic Change* (2025) 178:125, DOI: 10.1007/s10584-025-03970-z, https://cdn.cloud.prio.org/files/fdd4e7ad-ad28-4f4b-acc2-ad7d1073606b/s10584-025-03970-z.pdf?inline=true — scientific uptake in UNSC debates 2007–2022; AR6 average climate effect on conflict judged weak at present, more prominent with additional warming.
16. NATO (2021). "NATO Climate Change and Security Action Plan." 14 June 2021. https://www.nato.int/en/about-us/official-texts-and-resources/official-texts/2021/06/14/nato-climate-change-and-security-action-plan — verified live.
17. NATO. "Environment, climate change and security." https://nato.int/en/what-we-do/wider-activities/environment-climate-change-and-security — verified live.
18. United Nations Environment Programme (2009). *From Conflict to Peacebuilding: The Role of Natural Resources and the Environment.* ISBN 978-92-807-2957-3. https://preview-www.cbd.int/financial/doc/unep-conflict.pdf — index.
19. United Nations Environment Programme (2024). *Nature-based Solutions for Peace: Emerging practice and options for policymakers.* Nairobi. ISBN 978-92-807-4204-6. https://wedocs.unep.org/bitstreams/f4db3bd7-e326-481d-af02-4ea887583ff4/download — index.
20. SLSA. "Build: Requirements for producing artifacts." Specification v1.2. https://slsa.dev/spec/v1.2/build-requirements — verified live.
21. Filigrane (2026-07-15). "Blockchain Notarization: When Anchoring Hashes Makes Sense." https://www.filigrane.com/blockchain-notarization — verified live.
22. Bardwell-Scott, M. (2026). "A Cryptographically Signed Biography for Physical Hardware: Tamper-evident chain of custody for the AI and critical-infrastructure supply chain." Sovereign Proof Technical White Paper v1.3, October 2026. https://sovereignproof.io/sovereign-proof-whitepaper.pdf — verified live; vendor white paper, not peer-reviewed.
23. Regenscheid, A. (NIST) (2018). *Platform Firmware Resiliency Guidelines.* NIST SP 800-193, Final, May 2018. Summarised at https://www.electronicdesign.com/technologies/industrial/article/55367149/infineon-technologies-secure-tomorrows-data-centers-with-platform-firmware-resiliency and https://softwsp.com/guides/nist-sp-800-193-platform-firmware-resiliency/ — index.
24. Sigstore / SLSA / in-toto secondary guides (index, use primary specs for citation): https://dev.to/kamal_namdeo/slsa-sigstore-and-provenance-complete-practical-guide-1bl5 ; https://blog.michaelsam94.com/supply-chain-security-slsa-sbom/ ; https://hld.handbook.academy/curriculum/security-at-scale/supply-chain-security/ — index.
25. STAMP: "Synthesis Tamper-evident Attestation and Molecular Provenance (STAMP): Cryptographic Molecular Barcoding for DNA Synthesizers." Manuscript PDF. https://framerforms.s3.us-east-1.amazonaws.com/form-uploads/761ee2a5-94a2-4849-b65f-14b43cabbc10-stamp-cryptographic-molecular-barcoding.pdf — index; preprint, authors not captured.
26. Foster, D. & Clapper, A. "Swim, Swarm, Strike: Biomimetic War Machines and the Cyborg Ecologies of Perpetual Counterinsurgency." Conference paper. https://nomadit.co.uk/conference/pollen2026/paper/94200 — index.
