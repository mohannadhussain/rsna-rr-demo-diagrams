# Team Cormack
## Chest CT Flow Chart

```mermaid
flowchart LR
    Generator[Demo Generator] --> |1 DICOM| Qvera[Qvera Interface Engine]
 
    Qvera --> |2a ORM| Paxera
    Qvera --> |2b ORM| SmartReporting
    Qvera --> |2c DICOM| Paxera
    Qvera --> |2d DICOM| Fovia
    Qvera --> |2e DICOM| ACRAssess
    Qvera --> |2f FHIR Resources for GEIP| HAPI_FHIR
 
    Qvera --> |3a DICOM Study| CorelineAVIEW
    Qvera --> |3b DICOM Study| SiemensAIRC[Siemens AI Rad Companion]
 
    CorelineAVIEW --> |4a DICOM Results| Qvera
    SiemensAIRC --> |4b DICOM Results| Qvera
 
    %% As result data needs to be reviewed, it should only send to Fovia for review
    Qvera --> |5a Raw DICOM Results| Fovia
    Qvera --> |5b Raw DICOM Results| Paxera
    %% Tentative - Brian to confirm if he can do FHIR
    Qvera --> |5c Raw FHIR/DICOM Results| ACRAssess
    Qvera --> |5d ORM Prioritization| Paxera
   
    Fovia --> |6 Review Results| Fovia
 
    %% Results combining to happen in Fovia - different results
    Fovia --> |7 Combine Results| Fovia
   
    %% return results
    Fovia --> |8 Reviewed DICOM Results| Qvera
 
    %% distribute results
    %% Share over FHIRcast instead?!?
    Qvera --> |9 Reviewed ORU Results| SmartReporting
 
    SmartReporting --> |10a ORU| Paxera
    SmartReporting --> |10b ORU| Qvera

    %% Tentative - Brian to confirm if he can do FHIR
    Qvera --> |11 ORU| ACRAssess
```
