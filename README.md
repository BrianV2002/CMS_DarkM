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

| Primary dataset | Era      | Formato   | Enlace                                                                                   |
| --------------- | -------- | --------- | ---------------------------------------------------------------------------------------- |
| SingleMuon      | Run2016G | NANOAODv9 | /SingleMuon/Run2016G-UL2016\_MiniAODv2\_NanoAODv9-v1/NANOAOD ([opendata.cern.ch][1])     |
| SingleMuon      | Run2016H | NANOAODv9 | /SingleMuon/Run2016H-UL2016\_MiniAODv2\_NanoAODv9-v1/NANOAOD ([opendata.cern.ch][2])     |
| SingleElectron  | Run2016G | NANOAODv9 | /SingleElectron/Run2016G-UL2016\_MiniAODv2\_NanoAODv9-v1/NANOAOD ([opendata.cern.ch][3]) |
| SingleElectron  | Run2016H | NANOAODv9 | /SingleElectron/Run2016H-UL2016\_MiniAODv2\_NanoAODv9-v1/NANOAOD ([opendata.cern.ch][4]) |
| MET             | Run2016G | NANOAODv9 | /MET/Run2016G-UL2016\_MiniAODv2\_NanoAODv9-v1/NANOAOD ([opendata.cern.ch][5])            |

[1]: https://opendata.cern.ch/record/30530?utm "SingleMuon/Run2016G-UL2016_MiniAODv2_NanoAODv9-v1/NANOAOD"
[2]: https://opendata.cern.ch/record/30563 "/SingleMuon/Run2016H-UL2016_MiniAODv2_NanoAODv9-v1/NANOAOD | CERN Open Data Portal"
[3]: https://opendata.cern.ch/record/30529? "SingleElectron primary dataset in NANOAOD format ..."
[4]: https://opendata.cern.ch/record/30562?utm "SingleElectron primary dataset in NANOAOD ..."
[5]: https://opendata.cern.ch/record/30526 "/MET/Run2016G-UL2016_MiniAODv2_NanoAODv9-v1/NANOAOD | CERN Open Data Portal"


Los datasets se descargan directamente desde [https://opendata.cern.ch](https://opendata.cern.ch).

## Simulation


## Datasets (CMS Open Data, UL2016 — NANOAODv9)

| Grupo       | Subgrupo                | Dataset (UL2016)                                                        | Tipo | Formato     | Link oficial |
|-------------|-------------------------|-------------------------------------------------------------------------|------|-------------|--------------|
| tt          | —                       | TTToSemiLeptonic_TuneCP5_13TeV-powheg-pythia8                          | MC   | NANOAODSIM  | https://opendata.cern.ch/record/65498 |
| tt          | —                       | TTToHadronic_TuneCP5_13TeV-powheg-pythia8                              | MC   | NANOAODSIM  | https://opendata.cern.ch/record/69927 |
| t+X         | t-channel (top)         | ST_t-channel_top_4f_InclusiveDecays_TuneCP5_13TeV-powheg-madspin-pythia8| MC   | NANOAODSIM  | https://opendata.cern.ch/record/64763 |
| t+X         | t-channel (antitop)     | ST_t-channel_antitop_4f_InclusiveDecays_TuneCP5_13TeV-powheg-madspin-pythia8 | MC | NANOAODSIM | https://opendata.cern.ch/record/64669 |
| t+X         | tW (top)                | ST_tW_top_5f_NoFullyHadronicDecays_TuneCP5_13TeV-powheg-pythia8        | MC   | NANOAODSIM  | https://opendata.cern.ch/record/64895 |
| t+X         | tt̄V (TTW)              | TTWJetsToLNu_TuneCP5_13TeV-amcatnloFXFX-madspin-pythia8                | MC   | NANOAODSIM  | https://opendata.cern.ch/record/68073 |
| t+X         | tt̄V (TTZ)              | TTZToLLNuNu_M-10_TuneCP5_13TeV-amcatnlo-pythia8                         | MC   | NANOAODSIM  | https://opendata.cern.ch/record/68195 |
| W+jets      | HT-400–600              | WJetsToLNu_HT-400To600_TuneCP5_13TeV-madgraphMLM-pythia8               | MC   | NANOAODSIM  | https://opendata.cern.ch/record/69729 |
| W+jets      | FxFx (2J)               | WJetsToLNu_2J_TuneCP5_13TeV-amcatnloFXFX-pythia8 (**índice de archivos**) | MC | NANOAODSIM | https://opendata.cern.ch/record/69719/file_index/CMS_mc_RunIISummer20UL16NanoAODv9_WJetsToLNu_2J_TuneCP5_13TeV-amcatnloFXFX-pythia8_NANOAODSIM_106X_mcRun2_asymptotic_v17-v1_70000_file_index.txt |
| Z(ℓℓ)+jets | Inclusive DY            | DYJetsToLL_M-50_TuneCP5_13TeV-madgraphMLM-pythia8                      | MC   | NANOAODSIM  | https://opendata.cern.ch/record/35541 |
| Z(ℓℓ)+jets | Alta pT(Z)              | DYJetsToLL_M-50_Zpt-200toInf_BPSFilter_TuneCP5_13TeV-madgraphMLM-pythia8 (**índice de archivos**) | MC | NANOAODSIM | https://opendata.cern.ch/record/35675/file_index/CMS_mc_RunIISummer20UL16NanoAODv9_DYJetsToLL_M-50_Zpt-200toInf_BPSFilter_TuneCP5_13TeV-madgraphMLM-pythia8_NANOAODSIM_106X_mcRun2_asymptotic_v17-v2_260000_file_index.txt |
| Z(νν)+jets | HT-200–400              | ZJetsToNuNu_HT-200To400_TuneCP5_13TeV-madgraphMLM-pythia8               | MC   | NANOAODSIM  | https://opendata.cern.ch/record/36174 |
| VV, VH      | WW                      | WW_TuneCP5_13TeV-pythia8                                               | MC   | NANOAODSIM  | https://opendata.cern.ch/record/72696 |
| VV, VH      | ZZ                      | ZZ_TuneCP5_13TeV-pythia8                                               | MC   | NANOAODSIM  | https://opendata.cern.ch/record/75593 |
| VV, VH      | WZ                      | WZ_TuneCP5_13TeV-pythia8                                               | MC   | NANOAODSIM  | *(usar patrón de WW/ZZ si falta página)* |



For the signal, it is necessary to generate it locally using MadGraph 5 and simulate the detector with Delphes or CMSSW.

it is advisable to first focus on the background processes that do have publicly available datasets: W+jets, Z→ℓℓ, tt̄ (even if it is a 2015 version), multijet QCD, and GJets. These are the main contributors to the MET distribution in the control regions (CRs) and are essential for validating event selection. If the 2016 datasets are unavailable, it is acceptable to use the 2015 datasets as an approximation, provided that the differences are clearly documented. As a good practice, it is recommended to visually validate the obtained histograms by comparing them with the expected distributions from 2016 campaigns to verify their overall consistency.

For processes not available in Open Data, such as Single Top, VV (dibosons), and TTV (ttW, ttZ), two paths can be taken: simulating the events using generators such as MadGraph in conjunction with Pythia and Delphes, or applying data-driven estimation methods, although the latter can be more complex and less accurate for educational analysis. For the dark matter signal (tt̄+DM), it is recommended to use simplified public models such as those in the DMSimp repository (UFO) and generate the samples directly. When documenting the analysis, it is crucial to clarify which backgrounds were used, which were omitted, and how they were replaced or simulated, in addition to specifying the signal configurations used and the limits derived from the use of different campaigns between 2015 and 2016.

## Julie's suggestion

[Simulated dataset TTToSemiLeptonic](https://opendata.cern.ch/record/67993)
