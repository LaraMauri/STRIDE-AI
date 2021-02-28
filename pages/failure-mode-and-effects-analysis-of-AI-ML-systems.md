# Failure Mode and Effects Analysis of AI-ML Systems

## Background on FMEA
Failure Mode and Effects Analysis (FMEA) is a structured approach to discovering potential failures that may exist within the design of a product or process. Failure modes are the ways in which an asset (be it a process, system or component) can fail. Effects are the ways that these failures can lead to waste, defects or harmful outcomes for the customer. Failure Mode and Effects Analysis is designed to identify, prioritize and limit these failure modes.

## Guide to FMEA application in the AI-ML lifecycle
**Purpose**: Applying Failure Mode Effects Analysis (FMEA) to an AI-ML asset includes the following activities:
1. Assigning functions to the asset. 
2. Creating structure, function, networks diagrams for the asset. 
3. Define defects that can cause the asset’s function/function network to fail (Failure Modes, FMs)
4. Perform threat modeling actions (use STRIDE-AI Threat Modeling to map causes of FMs to threats).


_Step 1_: Create one function list per asset. The content of these function lists should be different for each asset in at least a function.

_Step 2_: Specify prerequisites for the functions that can to refer to functions of other assets. This is the basis used to create function networks.

_Step 3_:  Identify one or more asset defects that can impair a function (Failure Mode - FM). Add one or more causes or effects for each defect.

_Step 4_:  Use a Threat-modeling methodology to map FM to Threats.

**Severity**: A severity score can be assigned to FMs based on the effects. This is done independently from the severity of the threats. However, to ensure that the evaluations are consistent, it is advised that FM severity is passed on from the FMs to the threats associated to them, e.g. as a lower bound to DREAD-estimated severity.

**Roles**: Multiple roles are used when executing an FMEA, including Person responsible for the analysis, Person responsible for an asset category, Person responsible for actions, Participant, Other Interested parties.

## Question Facilitator
As an aid for the FMEA, the following are possible questions to ask as part of the FMEA procedure. _**These questions are adapted from the book “Effective FMEAs”, written by Carl S. Carlson, published by John Wiley & Sons, ©2012, all rights reserved.**_

## Functions
**When identifying functions for System or Design FMEAs, refer to the AI-ML lifecycle and to the asset list of your application**
- “What is the primary purpose of this asset?”
- “What is the asset supposed to do? What must the asset not do?”
- What functions occur at the interfaces?” 
- “What is the standard of performance?”

## Failure Modes
**When identifying failures modes (FMs) refer to the architecture diagram of your AI-ML application**
- “In what way could the asset fail to perform its intended function?”
- “In what way could the asset perform an unintended function?”
- “What could go wrong with this asset?”
- “What could go wrong at the interfaces?”
- “What has gone wrong with this asset in the past?”
- “How could the asset be abused or misused?”
- “What concerns do you have with this asset?”

## Effects
**When identifying effects for FMs, refer to the FM list identified in the previous step**
- “What is the consequence of the failure?”
- “If the asset fails, what will be the consequences at the local level? At the next higher level? At the overall system level? At the end user?”
- “If the asset fails, what will the customer see, feel or experience?”
- “Will the asset failure cause potential harm to the end users?”
- “Will the asset  failurecause potential violation of regulations?”







