---
  title: "Red teaming Notes"
  weight: 1
  pre: "<b>1. </b>"
  chapter: true
---
TODO [RESOURCES]
LOLBAS -> Living Off The Land Binaries and Scripts
TTP -> Techniques, Tactics, Procedures
IOC -> Indicator of Comprimise

- Mitre Attack https://mitre-attack.github.io/attack-navigator/
- OST Map https://www.intezer.com/ost-map/#PowerShdll
- TIBER-EU https://www.ecb.europa.eu/pub/pdf/other/ecb.tiber_eu_framework.en.pdf
- mallable profiles  https://hstechdocs.helpsystems.com/manuals/cobaltstrike/current/userguide/content/topics/malleable-c2_main.htm?cshid=1062
The second behavioral use of CTI is analyzing behavior and actions of an adversaries' malware and tools to develop your offensive tooling that emulates similar behaviors or has similar vital indicators.

An example of this could be an adversary using a custom dropper. The red team can emulate the dropper by,

    Identify syscalls and API calls
    Identifying overall dropper behavior and objective
    Tampering with file signatures and IOCs

#### Red Team campaign
- identify framework and general kill orchestrating
- determione targeted adversary
- identify adversary's TTPs and IOCs
- map gathered threat intelligence to a kill chain or frameworks
- draft and maintain needed engagement documentation
- determine and use needed engagement resources (tools, C2 modification, domains, etc.)
