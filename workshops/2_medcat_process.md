# MedCAT process

A project requires the extraction of concepts from unstructured data, into a structured form, potentially with linkage to other structured data assets.

## Process diagram

```mermaid
%%{init: {'theme': 'neutral' } }%%
  flowchart TD
    A(["MedCAT annotation and
        training required"])-->B1["Define scope of annotation
            concepts and target terms"]
            
    B1-->B2["Provide MedCAT training 
            materials and live session"]
    B1-->B3["Evaluate overlap with 
            existing annotations"]
    B3-->B4["Define documents for inclusion"]

    B2-->C["Client annotation within 
                MedCAT trainer"]
    B4-->C

    C-->C1{"Sufficient number and 
    quality of annotations?"}
    C1-->|No|C
    C1-->|Yes|D1["Fine-tune MedCAT model"]
    
    D1-->D2["Model validation 
            for patient inclusion"]
    D1-->D3["Model validation
                on annotation test set"]
    D2-->E["Extract MedCAT annotations"]
    D3-->E

```