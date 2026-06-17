# Team Stoney Flow Chart

```mermaid
flowchart TD
    Generator[Demo Generator] --> |1 DICOM| Qvera[Qvera Interface Engine]
 
    Qvera --> |2a ORM| Epic
    Qvera --> |2b ORM| Ramsoft[Ramsoft Omega AI]
    Qvera --> |2c ORM| NT[Newton's Tree]
    Qvera --> |2d DICOM| Ramsoft
    Qvera --> |2e DICOM| NT

    NT --> |3 DICOM| MV[MediView XR90]

    Epic --> |Remote Ordering and Image Exchange?!?| Epic
```