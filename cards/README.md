The cards present in the IDEA folder have been taken from the FCC-config from winter 2023 branch:
https://github.com/HEP-FCC/FCC-config/blob/winter2023/FCCee/Delphes/card_IDEA.tcl

The main difference between cards is:
## Detector Cards Overview

| Card                     | Beam pipe X₀ | VTX barrel X₀ | VTX endcap X₀ | Comment                                 |
|---------------------------|--------------|---------------|---------------|----------------------------------------|
| card_IDEA.tcl             | 0.35276      | 0.0937        | 0.0937        | Baseline                                |
| heavierBP_100pc.tcl       | 0.17638      | 0.0937        | 0.0937        | Only beam pipe lighter (~half)          |
| lighterVXD_75pc.tcl       | 0.35276      | 0.374         | 0.374         | Vertex detector much heavier (~4×)      | 