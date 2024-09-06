# Infrastructure Ontology

## Description
### Purpose
In energy domain, a simplified infrastructure topology of the system should be described in order to deliver intelligent services. The infrastructure topology facilitates the description of an infrastructure in a flexible way by allowing to describe the infrastructure’s components and its relations. 
### Scope
Infrastructure ontology provides OWL classes and properties to allow infrastructure of an energy system to be described.
### Description
This Infrastructure Ontology helps to define the infrastructure system of OMEGA-X use cases. The main class is the system 
which can be a system kind or a system of interest. System Kind  is an abstract class encompassing the taxonomy of inftastructure systems. A system of interest can be a physical system, a virtual system, an equipment or a site. It will be instatiated for each specific system, for e.g. LithiumBattery, Narbone solar plant..; It may have a system configuration encompassing different properties of intreset, in general defined from the data sheet or from an initial configuration of the system.

 
New module can be created to define the infrastructure of a specific use case family. This new module should be aligned with the general infrastructure ontology.

## Competency Questions

### Querying Questions
| ID | Question in natural language | Example
|---|---|---|
| cq-1 |What is the identifier of specific system? | the id of a specific system |
| cq-2 |What is the system connected to a specific system? | A weather station  is connected to meter  |
| cq-3 |What is the location of a specific site? | the  geolocation of a solar plant|
| cq-4|What is the system configuratin of a specific equipment? | the configuration  of a specific battery includig the nominal charge voltage|
| cq-4|What are the systems of interest that have as kind an energy production system? | the list of system of intresests for the system kind energy production system|


### Inference Questions
| ID | Question in natural language | Example
|---|---|---|
| iq-1 | What are the systems connected to another system?| the list of systems connected via connected to target and connected to source relations|
| iq-2 | What are the system of inetrests having a specific system configuration?| the list of system of inetrests for having the same configuration|

## Glossary
### OMEGA-X Infrastructure
* [**infra:_System_**](https://w3id.org/omega-x/ontology/Infrastructure/System/)
A system is an abstract class that can be a system of ineterest or a system kind. A system can be connected to another system. Moroever, a system can consist of other systems.
* [**infra:_SystemOfInterest_**](https://w3id.org/omega-x/ontology/Infrastructure/SystemOfInterest/)
A system of intresest can be an equipment, a site, or any other physical or virtual system. A system of interest can have a system kind, a system configuration and/or a location.
* [**infra:_SystemKind_**](https://w3id.org/omega-x/ontology/Infrastructure/Kind/)
The system kind classes describe the taxonomy of the energy infrastructure. More detailed view of this taxonomy is depicted in ......
* [**infra:Equipment**](https://w3id.org/omega-x/ontology/Infrastructure/Equipment/)
An equipement is a physical system which is part of the infrastructure.An equipment may be, for instance, an inverter or an electric vehicle charging station.
* [**infra:Site**](https://w3id.org/omega-x/ontology/Infrastructure/Site/)
A site is a part of the physical world or a virtual world that is inherently both located in this world and having a 3D spatial extent. It can include more than one equipment.A site may be, for instance, a solar plant or an electric vehicle charging station pool.
* [**infra:SystemConfiguration**](https://w3id.org/omega-x/ontology/Infrastructure/SystemConfiguration/)
A system configuration is a set of properties of interest characterizing its structure and behavior. In case of an equipment, it may reflect its datasheet.
## OWL Description
![Diagram](./Omega-X[v1.1]-Infra [V1.1].png)
# Recommendations
- A `infra:SystemOfInterest` can be an `eds:EvaluationPoint` (see [_EvaluationPoint_](../Energy Data Set Ontology) once an energy data set is attached to it. 
- The static attributes of an `infra:Syste` can be defined in `infra:SystemConfiguration`. 
- A `infra:SystemOfInterest` can have a location. 
- A `infra:System` can consist of an another  `infra:System` or many  `infra:System`.
- A An `infra:System` can be connected to another An `infra:System`. To precise the direction of the connection the object properties `infra:isConnectedTo` and An `infra:isConnectedFrom`
- Use case Families ontologies can create, specialize, and categorize system kinds.
- System kinds can be organized in a taxonomy using object properties  skos:narrower and skos:broader.
## Related Work
### SEAS
* [**_seas:System_**]( https://w3id.org/seas/System): The class of systems, i.e., systems virtually isolated from the environment, whose behaviour and interactions with the environment are modeled.

* [**_seas:connectedTo_**]( https://w3id.org/seas/connectedTo): Links a system to a system it is connected to. Connected systems interact in some way. The exact meaning of interact is defined by sub properties of [**_seas:connectedTo_**]. 

### SAREF4SYST
* [**_s4syst:System_**]( https://saref.etsi.org/saref4syst/System): he class of systems, i.e., systems virtually isolated from the environment, whose behaviour and interactions with the environment are modeled. Systems can be connected to other systems. Connected systems interact in some ways. Systems can also have subsystems. Properties of subsystems somehow contribute to the properties of the supersystem.

* [**_s4syst:connectedTo_**]( https://saref.etsi.org/saref4syst/connectedTo): Links a system to a system it is connected to. Connected systems interact in some way. The exact meaning of "interact" is defined by sub properties of [**_s4syst:connectedTo_**]. It is symmetric. This property can be qualified using class [**_seas:connection_**], which connects the two systems. If there is a connection between several systems, then one may infer these systems are pairwise connected.

