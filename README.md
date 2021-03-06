# Clas Clara Engine

Clas12 specific framework to design Clara service engines. Supports
developing engines for data processing, data analyses and data monitoring
services.

### Clara YAML configuration support

```
---
io-services:
  reader:
    class: org.jlab.clas12.convertors.CustomReader
    name: CustomReader
  writer:
    class: org.jlab.clas12.convertors.CustomWriter
    name: CustomWriter
    lang: cpp

services:
  - class: org.jlab.clas12.services.ECReconstruction
    name: ECReconstruction
  - class: org.jlab.clas12.services.SeedFinder
    name: SeedFinder
  - class: org.jlab.clas12.services.HeaderFilter
    name: HeaderFilter
    lang: cpp
  - class: org.jlab.clas12.services.FTOFReconstruction
    name: FTOFReconstruction

mime-types:
  - binary/data-evio
  - binary/data-hipo

configuration:
  global:
    magnet:
      torus: 10.75
      solenoid: 0.5
    ccdb:
      run: 10
      variation: custom
    kalman: true

  io-services:
    reader:
      block_size: 10000
    writer:
      compression: 2

  services:
    ECReconstruction:
      log: true
      layers:
        - inner
        - outer
    HeaderFilter:
      max_hits: 29
```