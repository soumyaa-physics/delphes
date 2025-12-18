The cards present in the IDEA folder have been taken from the FCC-config from winter 2023 branch:
[Delphes_FCCee_IDEA_card](https://github.com/HEP-FCC/FCC-config/blob/spring2021/FCCee/Delphes/card_IDEA.tcl)

The main difference between cards is:
## Detector Cards Overview

| Card                     | Beam pipe X₀ | VTX barrel X₀ | VTX endcap X₀ | Comment                                 |
|---------------------------|--------------|---------------|---------------|----------------------------------------|
| card_IDEA.tcl             | 0.35276      | 0.0937        | 0.0937        | Baseline                                |
| heavierBP_100pc.tcl       | 0.17638      | 0.0937        | 0.0937        | Only beam pipe lighter (~half)          |
| lighterVXD_75pc.tcl       | 0.35276      | 0.374         | 0.374         | Vertex detector much heavier (~4×)      | 

The main changes I made to the default idea card- card_IDEA.tcl is:

1. Set the exclusive clustering of jets to false- as we expect more jets 
2. added gravitno's PGDID in neutrino fiLter to account for MET:
  add PdgCode {1000049}
3. Added gravitinos in DualReadoutCalorimeter block 
    add EnergyFraction {1000049} {0.0 0.0}



To use key4hep do this everytime in k4SimDelphes:
```
source /cvmfs/sw-nightlies.hsf.org/key4hep/setup.sh
cd install
export PATH=$(pwd)/bin:${PATH}
export LD_LIBRARY_PATH=$(pwd)/lib64:${LD_LIBRARY_PATH}
```

Run the following code to combine delphes output with EDM4HEP:
```
DelphesHepMC_EDM4HEP  /eos/home-s/svashish/delphes/cards/IDEA/card_IDEA.tcl \
                      /eos/home-s/svashish/delphes/cards/IDEA/edm4hep_IDEA.tcl \
                      /eos/home-s/svashish/FCCAnalyses/examples/FCCee/bsm/LLPs/Stau/edm4hep_output/FCC_100stau_240COM.root \
                      /eos/home-s/svashish/MG5_aMC_v3_6_6/FCC_100stau_240com/Events/run_03/tag_1_pythia8_events.hepmc 
```

This script is placed in : ` k4SimDelphes/standalone/src/DelphesHepMC_EDM4HEP.cpp `