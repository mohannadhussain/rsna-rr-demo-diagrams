# Team Lauterbur
## Brain CT Flow Chart

See [clinical scenario](https://docs.google.com/document/d/1AbMGfBinw8_epP9_cIjC8s-tYXvqS_8XI4lB4wp4Qxc/edit?tab=t.0#heading=h.bxasmyukr250)

```mermaid
 flowchart LR
    %% Current CT acquisition
    Gen2[Demo Generator] --> |1 DICOM| QveraIE[Qvera Interface Engine]
    QveraIE --> |2a ORM| Epic[EpicRadiant]
    QveraIE --> |2b ORM| Visage[Visage]
    QveraIE --> |2c ORM| NT[NewtonsTree]
    QveraIE --> |2d ORM| RadAI[RadAI]
    QveraIE --> |2e DICOM| NT
    QveraIE --> |2f DICOM| ACR[ACRAssess]
    QveraIE --> |2g DICOM| Visage

    %% Send scan to icometrix
    NT --> |3 Prior or Current| iCo[icometrix AI]

    %% DICOM Results include SCs, PDF as well as SR with precent change
    iCo --> |4 DICOM Results| NT

    %% FHIR Reporting and Alerting
    NT --> |5a FHIR Observation| ACR
    NT --> |5b FHIR Observation| RadAI
    NT --> |5c HL7 v2 ORU| Epic

    NT --> |6a Check if Percent Change > Threshold| NT
    NT --> |6b Worklist Priorization HL7 v2 ORU| Epic

    %% Results distribution
    NT --> |7a DICOM Results| QveraIE
    NT --> |7b DICOM Results| Visage

    %% Reporting workflow
    Epic --> |8a FHIRcast Context Sync| Visage
    Epic --> |8b FHIRcast Context Sync| RadAI

    RadAI --> |9 Signed report ORU| Qvera

    Qvera --> |10a ORU| Visage
    Qvera --> |10b ORU| EpicRadiant
    Qvera --> |10c ORU| ACRAssess  
```
