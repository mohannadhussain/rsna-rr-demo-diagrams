# Team Lauterbur
## Brain MR Flow Chart

Requires multiple findings, one or more of which are modified or rejected, to implement [AIRA profile](https://www.ihe.net/uploadedFiles/Documents/Radiology/IHE_RAD_Suppl_AIRA.pdf).

```mermaid
flowchart TD
    Generator[Demo Generator] --> |1 DICOM| QveraIE[Qvera Interface Engine]

    QveraIE --> |2a ORM| EpicRadiant
    QveraIE --> |2b ORM| PACS
    QveraIE --> |2c ORM| NewtonsTree
    QveraIE --> |2d ORM| RadAI
    QveraIE --> |2e DICOM| NewtonsTree
    QveraIE --> |2f DICOM| ACRAssess

    NewtonsTree --> |3 DICOM Study| SiemensAIRC[Siemens AI Rad Companion]

    SiemensAIRC --> |4 DICOM Results| NewtonsTree

    NewtonsTree --> |5 Review Results IHE AIRA| ReviewResults[Review Results]
    ReviewResults --> |5a Apply AIRA Profile| NewtonsTree

    NewtonsTree --> |6a Modified DICOM w/ AIRA| QveraIE
    NewtonsTree --> |6b Modified DICOM w/ AIRA| PACS
    NewtonsTree --> |6c FHIR Results| ACRAssess
    NewtonsTree --> |6d FHIR Results| EpicRadiant
    NewtonsTree --> |6e FHIR Results| RadAI

    RadAI --> |7a ORU| PACS
    RadAI --> |7b ORU| EpicRadiant
    RadAI --> |7c ORU| ACRAssess

```
