# Team Lauterbur
## Brain MR Flow Chart

<!-- Would require multiple findings, one or more of which are modified or rejected, to implement [AIRA profile](https://www.ihe.net/uploadedFiles/Documents/Radiology/IHE_RAD_Suppl_AIRA.pdf). -->

```mermaid
flowchart LR
    Generator[Demo Generator] --> |1 DICOM| QveraIE[Qvera Interface Engine]

    QveraIE --> |2a ORM| EpicRadiant
    QveraIE --> |2b ORM| Visage
    QveraIE --> |2c ORM| NewtonsTree
    QveraIE --> |2d ORM| RadAI
    QveraIE --> |2e DICOM| NewtonsTree
    QveraIE --> |2f DICOM| ACRAssess
    QveraIE --> |2g DICOM| Visage

    NewtonsTree --> |3 DICOM Study| SiemensAIRC[Siemens AI Rad Companion]

    SiemensAIRC --> |4 DICOM Results| NewtonsTree

    NewtonsTree --> |5 Review Results| NewtonsTree

    NewtonsTree --> |6a DICOM Results| QveraIE
    NewtonsTree --> |6b DICOM Results| Visage
    NewtonsTree --> |6c FHIR Results| ACRAssess
    NewtonsTree --> |6d FHIR Results| RadAI
    NewtonsTree --> |6e HL7 v2 ORU| EpicRadiant

    RadAI --> |7 Signed report ORU| Qvera

    Qvera --> |8a ORU| Visage
    Qvera --> |8b ORU| EpicRadiant
    Qvera --> |8c ORU| ACRAssess  
```
