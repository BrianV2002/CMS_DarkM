# CMS_DarkM
Collection of ideas for a workshop to replicate dark matter analysis 1901.01553v2.pdf.

"This repository documents the attempt to replicate part of the [CMS-EXO-18-010](https://www.arxiv.org/pdf/1901.01553) analysis on the search for dark matter in proton-proton collisions at 13 TeV using CMS Open Data. Here you will find the datasets used, analysis scripts, event selection, and preliminary results based on public data."

## You can find the analysis note for it here on CADI (CMS Internal)
https://cms.cern.ch/iCMS/analysisadmin/cadilines?line=EXO-18-010&tp=an&id=2085&ancode=EXO-18-010


###  Datos 

| Dataset                             | Descripción                                   | Uso principal                      |
|-------------------------------------|-----------------------------------------------|------------------------------------|
| `MET/Run2016B-03Feb2017-vi`         | Eventos activados por triggers de MET         | Canal AH (0 leptón)                |
| `SingleMuon/Run2016B-03Feb2017-vi`  | Eventos con muones                            | Canal SL (1 muón), calibración     |
| `SingleElectron/Run2016B-03Feb2017-vi` | Eventos con electrones                      | Canal SL (1 electrón), validación  |

---

###  Simulaciones Monte Carlo

| Proceso            | Descripción                                             | Rol en el análisis                              |
|--------------------|---------------------------------------------------------|--------------------------------------------------|
| `tt + jets`        | Par de quarks top con jets adicionales                  | Fondo dominante en SL y AH                      |
| `single top`       | Producción individual de top (t-, s-, tW-canales)       | Fondo relevante, puede imitar la señal          |
| `W + jets`         | W bosón + jets, con leptones reales o mal identificados | Fondo en SL, especialmente con MET elevado      |
| `Z → ll`           | Z bosón decae a leptones                                | Validación y eficiencia de leptones             |
| `Z → νν`           | Z decae a neutrinos → solo MET                          | Principal fondo irreducible en AH               |
| `WW`, `WZ`, `ZZ`   | Dibosones                                               | Generan MET + leptones, fondo relevante          |
| `TTV`              | Procesos como ttW, ttZ                                  | Raros pero muy parecidos a la señal             |
| `QCD`              | Multijets                                               | Puede producir MET espurio por mala medición    |


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
| **W+jets**             | yes                        | [WJetsToLNu_13TeV-madgraphMLM-pythia8](https://opendata.cern.ch/record/69710)           | Campaña completa en 2016.                             |
| **Z/γ\* → ℓℓ**         | yes                        | [DYJetsToLL_M-50_13TeV-madgraphMLM-pythia8](https://opendata.cern.ch/record/35671)      | Fondo leptónico bien definido.                        |
| **tt̄ (HT 600–800)**   |  2015               | [TTJets_HT-600to800_13TeV-madgraphMLM-pythia8](https://opendata.cern.ch/record/19946)   | Usar como proxy si no se encuentra 2016.              |
| **tt̄ (SingleLept)**   |  2015               | [TTJets_SingleLeptFromT_13TeV-madgraphMLM-pythia8](https://opendata.cern.ch/record/19938) | Aprox válida si se justifica.                         |
| **QCD multijet**       |  mo          |         | Utilizable para validar colas de MET.                 |
| **GJets (fondo γ)**    |                        |                | Puede apoyar validación en CR hadrónicos.             |
| **Single top**         |2016 no disponible      | –                                                                                        | Buscar versiones 2015 o simular con MadGraph.         |
| **VV (WW, WZ, ZZ)**    | Parcial (2015)          | –                                                                                        | Se puede combinar manualmente desde Open Data 2015.   |
| **TTV (ttW, ttZ)**     | no                         | –                                                                                        | Simular si se desea alta precisión.                   |
| **Señal tt̄ + DM (ϕ → χχ)** | no                   | –                                                                                        | Simular con MadGraph + Pythia + Delphes.              |
| **Modelo simplificado**| ✅                         | [DMSimp_s_spin0 (FeynRules)](https://feynrules.irmp.ucl.ac.be/wiki/DMsimp)              | Base para simulación de señal.                        |


For the signal, it is necessary to generate it locally using MadGraph 5 and simulate the detector with Delphes or CMSSW.

it is advisable to first focus on the background processes that do have publicly available datasets: W+jets, Z→ℓℓ, tt̄ (even if it is a 2015 version), multijet QCD, and GJets. These are the main contributors to the MET distribution in the control regions (CRs) and are essential for validating event selection. If the 2016 datasets are unavailable, it is acceptable to use the 2015 datasets as an approximation, provided that the differences are clearly documented. As a good practice, it is recommended to visually validate the obtained histograms by comparing them with the expected distributions from 2016 campaigns to verify their overall consistency.

For processes not available in Open Data, such as Single Top, VV (dibosons), and TTV (ttW, ttZ), two paths can be taken: simulating the events using generators such as MadGraph in conjunction with Pythia and Delphes, or applying data-driven estimation methods, although the latter can be more complex and less accurate for educational analysis. For the dark matter signal (tt̄+DM), it is recommended to use simplified public models such as those in the DMSimp repository (UFO) and generate the samples directly. When documenting the analysis, it is crucial to clarify which backgrounds were used, which were omitted, and how they were replaced or simulated, in addition to specifying the signal configurations used and the limits derived from the use of different campaigns between 2015 and 2016.

## Julie's suggestion

[Simulated dataset TTToSemiLeptonic](https://opendata.cern.ch/record/67993)
