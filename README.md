# CMS_DarkM
Collection of ideas for a workshop to replicate dark matter analysis 1901.01553v2.pdf.

"This repository documents the attempt to replicate part of the [CMS-EXO-18-010](https://www.arxiv.org/pdf/1901.01553) analysis on the search for dark matter in proton-proton collisions at 13 TeV using CMS Open Data. Here you will find the datasets used, analysis scripts, event selection, and preliminary results based on public data."

## You can find the analysis note for it here on CADI (CMS Internal)
https://cms.cern.ch/iCMS/analysisadmin/cadilines?line=EXO-18-010&tp=an&id=2085&ancode=EXO-18-010

## Dataset
### Run2016

| Dataset | Enlace |
|--------------|--------|
| CMS Open Data Guide sobre selección de objetos MET | [CMS Open Data Guide](https://cms-opendata-guide.web.cern.ch/analysis/selection/objects/met/) |
| Dataset MET 2016 RunG en formato MINIAOD | [Acces](https://opendata.cern.ch/record/30509) |
| Dataset MET 2016 RunG en formato NANOAOD | [Acces](https://opendata.cern.ch/record/30526) |
| Dataset MET 2016 RunH en formato MINIAOD | [Acces](https://opendata.cern.ch/record/30542) |
| Archivo de configuración para el paso PAT (ReReco Run2016H MET UL2016 MiniAODv2) | [Ver configuración](https://opendata-qa.cern.ch/record/30453?utm) |
| Dataset SingleElectron 2016 RunG en formato MINIAOD | [Acces](https://opendata.cern.ch/record/30512) |
| Dataset SingleElectron 2016 RunH en formato MINIAOD | [Acces](https://opendata.cern.ch/record/30545) |

Los datasets se descargan directamente desde [https://opendata.cern.ch](https://opendata.cern.ch).

## Simulation

| Proceso               | Dataset Open Data (2016) | Enlace                                                                                  | Comentario / Alternativa                              |
|------------------------|---------------------------|------------------------------------------------------------------------------------------|--------------------------------------------------------|
| **W+jets**             | ✅                         | [WJetsToLNu_13TeV-madgraphMLM-pythia8](https://opendata.cern.ch/record/69710)           | Campaña completa en 2016.                             |
| **Z/γ\* → ℓℓ**         | ✅                         | [DYJetsToLL_M-50_13TeV-madgraphMLM-pythia8](https://opendata.cern.ch/record/35671)      | Fondo leptónico bien definido.                        |
| **tt̄ (HT 600–800)**   | ⚠️ Solo 2015               | [TTJets_HT-600to800_13TeV-madgraphMLM-pythia8](https://opendata.cern.ch/record/19946)   | Usar como proxy si no se encuentra 2016.              |
| **tt̄ (SingleLept)**   | ⚠️ Solo 2015               | [TTJets_SingleLeptFromT_13TeV-madgraphMLM-pythia8](https://opendata.cern.ch/record/19938) | Aprox válida si se justifica.                         |
| **QCD multijet**       | ✅ (HT 1000–1500)          | [QCD_HT1000to1500_13TeV-madgraph-pythia8](https://opendata.cern.ch/record/5495)          | Utilizable para validar colas de MET.                 |
| **GJets (fondo γ)**    | ✅                         | [GJets_HT-600ToInf_13TeV-madgraph](https://opendata.cern.ch/record/5564)                | Puede apoyar validación en CR hadrónicos.             |
| **Single top**         | ❌ 2016 no disponible      | –                                                                                        | Buscar versiones 2015 o simular con MadGraph.         |
| **VV (WW, WZ, ZZ)**    | ⚠️ Parcial (2015)          | –                                                                                        | Se puede combinar manualmente desde Open Data 2015.   |
| **TTV (ttW, ttZ)**     | ❌                         | –                                                                                        | Simular si se desea alta precisión.                   |
| **Señal tt̄ + DM (ϕ → χχ)** | ❌                   | –                                                                                        | Simular con MadGraph + Pythia + Delphes.              |
| **Modelo simplificado**| ✅                         | [DMSimp_s_spin0 (FeynRules)](https://feynrules.irmp.ucl.ac.be/wiki/DMsimp)              | Base para simulación de señal.                        |


For the signal, it is necessary to generate it locally using MadGraph 5 and simulate the detector with Delphes or CMSSW.

it is advisable to first focus on the background processes that do have publicly available datasets: W+jets, Z→ℓℓ, tt̄ (even if it is a 2015 version), multijet QCD, and GJets. These are the main contributors to the MET distribution in the control regions (CRs) and are essential for validating event selection. If the 2016 datasets are unavailable, it is acceptable to use the 2015 datasets as an approximation, provided that the differences are clearly documented. As a good practice, it is recommended to visually validate the obtained histograms by comparing them with the expected distributions from 2016 campaigns to verify their overall consistency.

For processes not available in Open Data, such as Single Top, VV (dibosons), and TTV (ttW, ttZ), two paths can be taken: simulating the events using generators such as MadGraph in conjunction with Pythia and Delphes, or applying data-driven estimation methods, although the latter can be more complex and less accurate for educational analysis. For the dark matter signal (tt̄+DM), it is recommended to use simplified public models such as those in the DMSimp repository (UFO) and generate the samples directly. When documenting the analysis, it is crucial to clarify which backgrounds were used, which were omitted, and how they were replaced or simulated, in addition to specifying the signal configurations used and the limits derived from the use of different campaigns between 2015 and 2016.
