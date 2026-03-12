### Solution Design
This guide describes the processes and best practices in creating and managing solution design document.

Solution design document is the living document of an initiative. It contains comprehensive information about what changes being introduced, why this is  important to be implemented, and how will this be built before the actual implementation proceeds.

There are 2 main parts in this document:

1. Solution background
2. Solution Architecture

<b> When do we consider creating solution design document? </b>

There are 3 things to ask ourselves:

1. Will the change have significant structural impact in the platform? (e.g., creating a new microservice, or impacting non-functional characteristics like scalability, performance, or security). If it does, then create it!

2. Will the change have significant effort? If the change requires engineering and testing with effort estimated to 2 sprints or beyond, then create it!

3. Will the change introduce new technology or vendor? If it requires to integrate with new technology or 3rd party vendor that is new to existing architecture, then create it!

> See actual template below

### Solution Design - "{Initiative title}"

#### Solution Background

##### Context *
> This section describes the "What" and "Why" of this initiative. 

> Provide a brief summary of the problem statement. Indicate details why this is important to build. What business and platform capability does it enable? Provide the key business drivers and their use case.

##### Current State *
> Start describing the current state (existing architecture) first. What are its limitation and challenges. Provide a diagram here.

##### Scope *

> This section describes the changes included in this solution and what explicitly excluded. This is to manage expectations.

In Scope *
| ID | Feature / Functionality |
| --- | --- |

Out Scope *
| ID | Feature / Functionality | Exclusion Reason |
| --- | --- | --- |

##### Key Functional Requirements
> What are the functional requirements that shape this solution design? A functional requirement must follow this format "As a {user}, I want to {use case}, so that {result}"

| ID | Functional Requirement |
| --- | --- |

##### Non-Functional Requirements
> This defines the end-user / customer experience by setting the performance and reliability targets (NFRs). (e.g., availability, latency, security, etc.)  

##### Assumptions
> List down all technical and/or business assumptions.

| ID | Assumption | Implication | Confirmed |
| --- | --- | --- | --- |
|  |  | Note the implication if proven false | Use a status label then provide a link or reference |

##### Constraints
> List down all technical and/or business limitations / constraints. (e.g., budget, resources, governance, etc.)

| ID | Constraint | Implication |
| --- | --- | --- | 
| | | Implication of this limitation to the solution |

##### Solution Options
> Provide a side-by-side comparison among options that are considered in shaping this solution.

| Section | Option 1 | Option 2 |
| --- | --- | --- |
| Description |
| Pros & Cons |
| Risk |
| Estimated cost and effort |

##### Key Design Decisions
> List the key design decisions that influence this solution

| Decision | Rationale | Alternative Considered | 
| --- | --- | --- |

##### Risks
> Call out any technical, security, performance, and other risks introduced by this solution and how they are mitigated

| Risk | Probability | Impact | Mitigation | Risk Score
| --- | --- | --- | --- | --- |
| Risk format "If {cause}, then {effect}"

#### Solution Architecture
> This section describe the "How" will the solution be implemented. This provides high-level architecture diagram.

##### Platform diagram
> This shows the physical diagram, components where your solution is built. For instance, AWS or GCP managed services, etc.

##### Logical diagram
> This shows the interaction between components, more focused on the business logic. We can leverage different diagrams here, for example, sequence diagrams, flowchart, etc.

#### Other considerations
##### Security consideration
##### Scalability consideration
##### Data models
##### Test strategy
##### Monitoring
##### Error handling
##### Release process