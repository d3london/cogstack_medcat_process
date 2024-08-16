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

## Workshop outcomes

### Initial annotation/document review and set-up 
* Annotation index as dashboard:
  * Potential to pass entire index for visualisation
  * What is depth of human annotation across different clinical domains / SNOMED code areas?
  * What is depth along tree level
  * What is gap for each project?
* Initial scoping searches on Elastic between Client and Analyst
* From jupyter notebook to app-based setup:
  * Move to a webapp for project set up?
  * Build queries, select and pass into MedCAT trainer
  * Queries saved to library 

### User training
* Upgrading training:
  * Update to written materials - process driven
  * New video recordings?

### Model registration and lineage 
* Enabling lineage 
  * Per project annotations assigned ID (or set of IDs)
  * Attach to model IDs
  * Possible for all projects to feed into model registry
  * Host registry in cloud (cross-site)  

### Validation
* Validation based on patient-level outcome recorded as model metadata
* After human annotation in project, ?keep test set of documents
  * Introduce routine per-concept annotation validation
  * Introduce negative document samples for false positive rate