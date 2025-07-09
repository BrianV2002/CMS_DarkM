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

| Dataset | Enlace | ¿Disponible? | Alternativa |
|--------|--------|---------------|-------------|
| `WJetsToLNu_012JetsNLO_34JetsLO_EWNLOcorr_13TeV-sherpa` (W+jets) | [Acces](https://opendata.cern.ch/record/69710) | yes | – |
| `DYJetsToLL_M-50_13TeV-madgraphMLM-pythia8` (Z/γ* → ℓℓ) | [Acces](https://opendata.cern.ch/record/35671) | yes | – |
| `TTJets_HT-600to800_13TeV-madgraphMLM-pythia8` (tt̄ fondo, versión 2015) | [Acces](https://opendata.cern.ch/record/19946) | yes (2015) | Usar como aproximación si 2016 no está |
| `TTJets_SingleLeptFromT_TuneCUETP8M1_13TeV-madgraphMLM-pythia8` | [Acces](https://opendata.cern.ch/record/19938) | yes (2015) | – |
| `QCD_HT1000to1500_13TeV-madgraph-pythia8` (QCD multijet ejemplo) | [Acces](https://opendata.cern.ch/record/5495) | Parcial | Simular o usar estimación data-driven |
| `GJets_HT-600ToInf_13TeV-madgraph` (fondo fotónico instrumental) | [Acces](https://opendata.cern.ch/record/5564) | yes | – |
| **Señal tt̄ + DM (φ → χχ)** | – |  No disponible |  Simular con MadGraph + PYTHIA + Delphes |
| Modelo simplificado para MadGraph (UFO) | [DMSimp_s_spin0 (FeynRules)](https://feynrules.irmp.ucl.ac.be/wiki/DMsimp) | yes | – |

Para la señal, es necesario generarla localmente usando MadGraph 5 y simular el detector con Delphes o CMSSW.

