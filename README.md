# ARP v18: THE ULTIMATE CONSOLIDATED DRUG DISCOVERY PIPELINE

![Version](https://img.shields.io/badge/Version-18.0--ULTIMATE-blue)
![Date](https://img.shields.io/badge/Date-2026--04--12-green)
![Python](https://img.shields.io/badge/Python-3.8+-yellow)

---

## 🎯 Overview

**ARP v18** is the culmination of all ARP versions (v5-v17 + v-next), consolidating the **best modules** from each version into a single, unified pipeline.

### Philosophy: "All-in-One"

Every module that proved valuable across 17 previous versions has been integrated into v18.

---

## 📜 Version History & Module Origins

| Version | Key Innovations | Modules Consolidated |
|---------|-----------------|---------------------|
| **v5** | Multi-omics, Time-series | omicverse, timesfm, Literature KG |
| **v7** | RAG Systems, Peptides | LightRAG, Biomed RAG, Peptide Loop |
| **v10** | Advanced Retrieval | BM25, HyDE, IRCoT, Hybrid Search |
| **v12** | RL Refinement | CellFluxRL, FlashBind |
| **v13** | Literature Mining | Hyperbrowser, NIIA Memory |
| **v14** | 3D-aware Generation | Token-Mol (atom-SMILES), TF Atlas |
| **v15** | Validation | SMILES Validator, gbrain, Archon |
| **v16** | Graph Neural Networks | GPDRP GNN, AlphaSAXS, scPBPK |
| **v17** | Unified Scoring | GPDRP + AlphaSAXS + scPBPK |
| **v-next** | Novelty-First | LINCS L1000, Risk Assessment |

---

## 🔬 13-Phase Pipeline Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    ARP v18 PIPELINE                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Phase 0: LINCS L1000 Integration                               │
│           → Real transcriptomic data (1170 drugs, 51K perts)   │
│                                                                 │
│  Phase 1: Literature Risk Assessment ⚠️ NEW                     │
│           → Dual-role targets, context effects                  │
│                                                                 │
│  Phase 2: Multi-Omics Integration                               │
│           → omicverse, TF Atlas re-analysis                      │
│                                                                 │
│  Phase 3: Target Discovery                                      │
│           → Literature KG, LightRAG                             │
│                                                                 │
│  Phase 4: Hybrid Retrieval                                       │
│           → BM25 + HyDE + IRCoT                                 │
│                                                                 │
│  Phase 5: Virtual Screening                                     │
│           → FlashBind + Pharmacophore + NaturalChem DB          │
│                                                                 │
│  Phase 6: De Novo Generation                                    │
│           → Token-Mol + GPDRP GNN                               │
│                                                                 │
│  Phase 7: RL Refinement                                         │
│           → CellFluxRL (7-dimension multi-reward)              │
│                                                                 │
│  Phase 8: ADMET Prediction                                      │
│           → RDKit + NP-likeness + PAINS alerts                 │
│                                                                 │
│  Phase 9: GPDRP GNN Scoring                                     │
│           → Molecular graphs, GIN + Graph Transformer           │
│                                                                 │
│  Phase 10: AlphaSAXS + scPBPK                                   │
│            → SAXS + AlphaFold, Single-cell PBPK                │
│                                                                 │
│  Phase 11: Token-Mol Tokenization                               │
│            → Atom-in-SMILES, Torsion angles                    │
│                                                                 │
│  Phase 12: NIIA Memory Consolidation                             │
│            → Cross-session memory, Workspace consciousness     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🏆 Key Features

### 1. Literature Risk Assessment (NEW!)
```python
# Catches dual-role targets before clinical trials
Embelin → XIAP inhibition → WARNING (muscle degradation risk)
Setanaxib → NOX4 inhibition → WARNING (aging muscle harm)
```

### 2. Multi-Modal Integration
- **Transcriptomic**: LINCS L1000 real data
- **Structural**: FlashBind, AlphaSAXS, Token-Mol
- **Knowledge**: Literature KG, LightRAG, gbrain
- **Graph**: GPDRP GNN (molecular graphs > SMILES)

### 3. 7-Dimension RL Refinement
1. Pharmacophore
2. Bioactivity
3. Structure
4. ADMET
5. Novelty
6. Synthesis
7. Drug-likeness

### 4. Novelty-First Paradigm
```
Discover novel pathophysiology → Then novel drugs
NOT: Literature search → Screen known targets
```

---

## 📊 Scoring Weights

| Component | Weight | Source |
|-----------|--------|--------|
| Novelty | 25% | De novo generation |
| LINCS Score | 20% | Transcriptomic |
| Bioactivity | 15% | ChEMBL + Virtual screening |
| Structure | 10% | FlashBind, AlphaSAXS |
| Pharmacophore | 10% | Target-based matching |
| ADMET | 10% | RDKit + predictions |
| GPDRP | 5% | Graph neural network |
| AlphaSAXS | 5% | Structural dynamics |

---

## 🚀 Usage

```python
from arp_v18_orchestrator import ARPv18

# Initialize
arp = ARPv18(disease="sarcopenia", n_candidates=20)

# Run pipeline
results = arp.run()

# Save results
arp.save("sarcopenia_results.json")
```

### Command Line
```bash
python3 arp_v18_orchestrator.py -d sarcopenia -n 20 -o results.json
```

---

## 📁 Output Structure

```json
{
  "version": "18.0-ULTIMATE",
  "disease": "sarcopenia",
  "timestamp": "2026-04-12T22:48:00",
  "candidates": [
    {
      "id": "DE_NOVO_003",
      "name": "De Novo 3",
      "source": "denovo",
      "novelty": 0.95,
      "final_score": 0.72,
      "severity": "NONE",
      "risk_flags": []
    }
  ],
  "summary": {
    "total_candidates": 15,
    "lincs_candidates": 5,
    "denovo_candidates": 10,
    "high_risk_flags": 2,
    "top_candidate": "LINCS_Embelin"
  }
}
```

---

## ⚠️ Risk Assessment

The pipeline now includes **Literature Risk Assessment** that flags:

| Risk Type | Example | Detection |
|-----------|---------|-----------|
| Dual-role targets | NOX4 (aging vs inflammation) | Literature-based |
| Context effects | XIAP (muscle protection vs cancer) | JASN 2010 |
| Preclinical warnings | biorXiv 2026-03 | Preprint monitoring |

---

## 🧬 Module Source Locations

| Module | Original Location | v18 Integration |
|--------|------------------|-----------------|
| LINCS L1000 | arp-next/lincs_integrator.py | Phase 0 |
| Risk Assessment | arp-next/literature_risk_assessor.py | Phase 1 |
| Multi-omics | arp-v5/omicverse_integration.py | Phase 2 |
| Target Discovery | arp-v5/literature_kg.py | Phase 3 |
| BM25/HyDE/IRCoT | arp-v10/bm25_index.py, hyde_search.py, ircot_hypothesis.py | Phase 4 |
| FlashBind | arp-v12/flashbind_scorer.py | Phase 5 |
| Token-Mol | arp-v14/tokenmol/token_mol_wrapper.py | Phase 6 |
| CellFluxRL | arp-v12/cellfluxrl_refiner.py | Phase 7 |
| ADMET | arp-v10/admet_predictor.py | Phase 8 |
| GPDRP GNN | arp-v16/gpdrp_enhanced_gnn.py | Phase 9 |
| AlphaSAXS | arp-v16/alphasaxs_scpbpk_integration.py | Phase 10 |
| NIIA Memory | arp-v13/arp_niia.py | Phase 12 |

---

## 📈 Results Example (Sarcopenia)

```
 Top 5 Candidates:
  1. LINCS_Embelin (Embelin): 0.6610 ⚠️ HIGH RISK
  2. LINCS_Setanaxib (Setanaxib): 0.6315 ⚠️ HIGH RISK
  3. DE_NOVO_003 (De Novo 3): 0.6052 ✅ NOVEL
  4. DE_NOVO_000 (De Novo 0): 0.6031 ✅ NOVEL
  5. DE_NOVO_006 (De Novo 6): 0.5994 ✅ NOVEL

 Summary:
  Total: 15 candidates
  LINCS: 5 | De novo: 10
  High risk: 2
```

---

## 🔮 Future Directions

- [ ] Add preprint monitoring (biorXiv, medRxiv)
- [ ] Integrate AlphaFold3 for structure prediction
- [ ] Add clinical trial matching
- [ ] Multi-target deconvolution
- [ ] Patient-derived organoid screening

---

## 📚 References

| Module | Citation |
|--------|----------|
| LINCS L1000 | https://github.com/dhimmel/lincs |
| GPDRP | BMC Bioinformatics 10.1186/s12859-023-05618-0 |
| Token-Mol | Wang et al., Nature Communications (2025) |
| FlashBind | MLSB 2025 (AIDD-Lab) |
| CellFluxRL | arXiv papers (2024-2025) |

---

## 👥 Author

**ARP Pipeline Series** - Started 2026-03-28

Consolidated by: Demis (AI Assistant)  
For: Dr. OCM (오창명)

---

## 📄 License

Research use only. Not for clinical applications.

---

**Version: 18.0-ULTIMATE**  
**Date: 2026-04-12**  
**Philosophy: "All-in-One - Best of Every Version"**
