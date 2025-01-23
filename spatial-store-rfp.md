# Spatial App Store and Infrastructure Request for Proposals
# OMA3 Portaling and Mapping Working Group (PMWG)

## Introduction

This Request for Proposals (RFP) is released by OMA3’s Portaling and Mapping Working Group (PMWG). The purpose of this RFP is to solicit specification proposals for the Spatial Store and underlying infrastructure.  It is also a call for non-members with expertise in this area to join OMA3 and help build the Spatial Store.

The Spatial Store is defined by the Metaverse Standards Forum use case document entitled “[Spatial Store for 3D Virtual World Applications](https://docs.google.com/document/d/1Pq3e8mhmEYYjxcsgOrg1rS2F0ZjHwQRbjxq74zePDts/)”.  

Note that the Spatial Store itself is not a technical standard.  The infrastructure the Spatial Store is built on (also part of this RFP) will be a technical standard.  In other words, if OMA3 is successful, there could be multiple app stores that use the same infrastructure that the Spatial Store uses.

## Scope

This RFP leverages the MSF use case document referred to above, but uses different language that is more conducive to measuring the effectiveness of standards proposals.  This RFP creates a more formal description of actors and use case flows. The RFP then outlines high-level threats for circumventing the system.  The RFP finally details a comprehensive range of functional and non-functional requirements that both the Spatial Store and any new standards need to fulfill. However, this document does not delve into the architectural or design aspects of the system, as these will come from proposals submitted in response to this RFP. This RFP serves to offer a clear acceptance criteria that can be used to judge such specification proposals.

OMA3 members can respond to this RFP as follows:
  1. Fill out the [PMWG contribution form](https://docs.google.com/forms/d/e/1FAIpQLSdxoEfPjp0aidCIqhSj--3zm0DG0R9WE7Ed8cqlVUduvkjm3w/viewform).
  2. Contact batis@oma3.org[batis@oma3.org](mailto:batis@oma3.org) or roderick@simul.co.uk[roderick@simul.co.uk](mailto:roderick@simul.co.uk) to get your proposal on the PMWG meeting agenda or put your proposal in the [PMWG Contributions folder](https://drive.google.com/drive/folders/1gLdOreG5f7EbBru58eP8-8iKa1gc_iZ5?usp=share_link).

## Use Cases

For more information on the value of use cases, please see Section 3 of the [OMA3 Working Group Process](https://github.com/oma3dao/working-group-process/blob/main/working-group-process.md). 

Usually there are two main components of a use case definition- the system and actors.  However, in this case the system is split into two parts- the Store, which is an application that users interact with to navigate and participate in the open metaverse, and the Infrastructure, which implements new industry standards that the Store uses.  In this document we will refer to System (Store or Infrastructure), Store, and Infrastructure.

### Store

The Store is an application running on a device that end users interact with to discover, view, and use virtual worlds and utilities.  

### Infrastructure

The Infrastructure is the system that implements new and existing technical standards that are used by the Store. Examples of Infrastructure standards include an ID system for identifying Applications and End Users.

### Actors

In this RFP, the main actors are as follows:

  * End Users: Individuals who explore the 3D spatial app store to discover, download/stream, and use virtual world applications. They may interact with both spatial and non-spatial applications based on their needs and devices.
      * Agents:  a sub-Actor of End Users that are software bots or autonomous AI agents.  Agents can be owned by an End User or created by an End User that severs control of the Agent so it can operate autonomously.
  * Developers: Entities or individuals who create virtual world applications and register them in the app store. They are responsible for specifying their application's spatial location (if applicable) and ensuring compliance with cybersecurity standards.
  * Applications/Worlds: Virtual environments themselves, treated as entities in the metaverse. They are the locations within the spatial coordinate system where applications are hosted, allowing users to interact with or explore them.
  * Store Operator: The entity responsible for managing the spatial app store and the spatial coordinate system, handling cybersecurity certification, overseeing the registration and listing process, and ensuring cross-platform functionality.
  * Reviewer: Responsible for reviewing Applications and associating the review results with the Application.
  * Assessor:  Responsible for issuing credentials on an Actor, such as whether an End User is a human or Agent, or for cybersecurity compliance of an Application.
  * Platform Providers: Companies providing the operating systems and devices (iOS, Android, Oculus, Vision Pro, etc.) where worlds and versions of the spatial app store are deployed.
  * IWPS: The Inter World Portaling System, enabling users to seamlessly transition between virtual worlds.  IWPS is the mechanism the Store uses to allow a user to use a World and portal between worlds

![Figure1](https://github.com/oma3dao/spatial-store-rfp/blob/main/figure%201.png)  
_Figure 1. Main actors_  

### Use Case

Preconditions

  * Optional- System has defined a spatial coordinate system that has locations Worlds can occupy.
  * System has an ID system that tracks Applications and optionally End Users and Agents.
  * Optional- End User has credentials from an Assessor.
  * Store Operator has approved one or more Assessors and has made their contact information available to Developers.
  * Store Operator has published requirements for Application submission.

  1. Registration:  Developer registers Application with System and obtains an ID (if necessary).
  2. Addressing (optional): Developer acquires a location in the Infrastructure for their World. 
  3. Review: Developer requests an Assessor perform a review of the Application.  Assessor associates results with Application ID on System.
  4. Submission: Developer submits their Application to the Store Operator. 
  5. Approval: The Spatial Store Operator reviews the Assessor results. If the Application passes requirements, the Operator allows the Application to be listed in the Store.
  6. Listing: Once approved, the Application is officially listed in the Store.  If the Application is a World, it occupies its location within the Store’s 3D space.
  7. Use:  End User chooses an Application in the UI.
  8. Login:  End Users use System to identify and authenticate themselves with the Application.  Application optionally checks Assessor credentials to approve/reject login.
  9. Exploration: End Users access the Store using their device (e.g., VR headset, smartphone, or PC). The End User is presented with a 3D interface where they can explore available Worlds.  Agents either access the Store or the Infrastructure directly.
  10. Interaction: End Users navigate the Store space, discovering and interacting with different Worlds. When an End User clicks on a World, they can enter it using IWPS.
  11. Non-Spatial Apps: For utility Applications (e.g., crypto wallets) that do not require spatial placement, End Users can toggle the Store to a non-spatial view, where these Applications are listed in a traditional 2D interface.

## Threat Model

For more information on the value of a threat model, please see Section 4 of the [OMA3 Working Group Process](https://github.com/oma3dao/working-group-process/blob/main/working-group-process.md). The Spatial Store will encounter the following threats:

  1. Malicious Applications:  Adversaries could attempt to submit applications that contain malware, spyware, or ransomware, potentially compromising user devices or data once downloaded or accessed. Adversaries could create counterfeit versions of popular applications or worlds to deceive users
  2. Store Compromise:  Adversaries can compromise the Store through various attack vectors, including:  
      a. Compromising the mechanism the Store is accessed by users  
      b. Intercepting the Store download  
      c. Compromising the Store software  
      d. Attacking third-party tools, libraries, or development kits used by the Store  
  3. Infrastructure Compromise:  Vulnerabilities in smart contracts could be exploited to steal funds, change ownership of virtual worlds, or manipulate application functionality
  4. Supply Chain Compromise:  Adversaries can compromise system/protocol components.  
     Examples of such components include:  
      a. IWPS protocol, especially if Applications do not implement the highest level of security.  
      b. Web browser  
      c. Operating system  
      d. Third party application infrastructure connecting to the IWPS protocol.  
  5. Component Compromise:  Adversaries can attack a vulnerability in the System’s software bill of materials (SBOM).
  6. Location Spoofing and Hijacking: Attackers could exploit vulnerabilities in the Infrastructure spatial coordinate system to spoof or hijack registered locations such as:  
      a. Placing malicious applications in highly visible or trusted locations.  
      b. Taking away the location of a World.  
  7. Data Breaches:  
      a. Adversaries can steal data (including behavior, location, and interactions) stored by the Store.  
      b. Adversaries can misuse public information stored on the Infrastructure.  
  8. Cross-Platform Vulnerabilities: Since the app store will operate across various platforms (iOS, Android, VR, PC, etc.), vulnerabilities in one platform may allow attackers to compromise other platforms or the overall app store ecosystem.
  9. Denial-of-Service (DoS) Attack: Attackers could flood the Infrastructure with fake registration requests or excessive network traffic.
  10. Reputation Spoofing:  
      a. Attackers could register false credentials with an End User, such as an Agent as a human or a human as an Agent.  
      b. Attackers could register false credentials with an Application.  
  11. Identity Theft:  
      a. Attackers could steal or hijack the identity of an End User or Developer.  
      b. Attackers could view private credentials associated with an ID.  
      c. Attackers could track End Users through the metaverse, violating privacy rights.  

## Requirements

The below requirements are used as a measure to compare different System design options.  Some of the requirements are required, some are optional.  For more information on how to interpret the language, please see Section 5 of the [OMA3 Working Group Process](https://github.com/oma3dao/working-group-process/blob/main/working-group-process.md). 

  1. Interoperability Requirements  
      a. The Store SHALL be accessible from web browsers, iOS, and Android if allowed.  
      b. The Store SHALL support Applications built for web browsers, iOS, Android, MacOS, and Windows.  
      c. The Store MAY support Applications built on Linux based operating systems  
      d. The Store MAY support closed platforms like PS, Xbox, Oculus, and Vision Pro.  
      e. The Store SHALL use IWPS to launch Applications.  
      f. The Store SHALL allow portaling to it via IWPS.  
      g. The Infrastructure SHALL store ID registrations on the blockchain.  
      h. The Infrastructure SHALL store location registrations on the blockchain.  
      i. The Infrastructure SHOULD support the most common spatial addressing industry standards.  
      j. The Infrastructure SHOULD have the ability to support all blockchains.  
      k. The Infrastructure ID system SHOULD support the DID standard.  
  2. Scalability:  
      a. The Store SHOULD support thousands of Applications.  
      b. The Infrastructure SHOULD support millions of locations and IDs.  
  3. Cybersecurity Requirements:  
      a. The Store SHOULD support a clear, transparent, and fair cybersecurity certification program.  
      b. The cybersecurity program SHOULD allow for multiple review mechanisms.  
  4. Governance:
      a. Governance of the System SHALL be controlled by OMA3.  
      b. The System governance SHALL have dispute resolution mechanisms for location ownership and ID registration.  
      c. The Store application submission requirements SHALL be clearly defined and applied.  
  5. Regulatory and Compliance Requirements:  
      a. System SHALL conform to regulations in jurisdictions the Store is made available.  
      b. This System SHALL comply with all applicable privacy and data protection regulations including GDPR, CCPA, and COPPA.  
      c. The Store SHOULD maintain industry-standard security measures to protect user data and follow platform-specific security guidelines.  
      d. The Store MAY implement accessibility requirements and standards to ensure usability for all users.  
      e. The System SHALL adhere to all relevant app store policies, guidelines, and content restrictions of the Platform it resides on.  
  6. User Privacy and Data Security:  
      a. Compliance with global privacy regulations, such as the General Data Protection Regulation (GDPR) in Europe and California Consumer Privacy Act (CCPA) in the US.  
      b. Strong data security protocols to ensure the safe handling of user data, including anonymization and encryption technologies.  
  7. Store  
      a. The Store SHALL have a 3D view for navigating XR Worlds  
      b. The Store SHALL have a 2D or 3D view for navigating 3D applications that do not require XR.   
      c. The Store SHALL have a 2D view for navigating Applications  
  8. ID and Reputation:  
    a. The ID system MUST identify Applications.  
    b. The ID system SHOULD identify Developers.  
    c. The ID system SHOULD identify human End Users.  
    d. The ID system MAY identify Agents and other non-human entities, including:  
       - Who controls the Agent.  
       - Who created the Agent.  
    e. The ID system MUST provide a mechanism to store reputation credentials with an ID.  
       - The reputation mechanism SHOULD allow selected data to be access controlled by the entity behind the owning ID.  
       - Reputation credentials SHOULD include humanity attestation.  
       - Reputation credentials SHOULD include cybersecurity information on an Application.  
    f. The ID system SHOULD provide a mechanism for the Developer to associate metadata with their Application, including:  
       - Regions (e.g.- countries, continents, etc.).  
       - Language support.  
    g. If the ID system supports identity for Users, the ID system MAY be able to leverage a User’s login credentials (e.g.- email address or wallet address) for a specific Application for login purposes.
       - The login mechanism SHOULD allow a User to keep their login credentials private and controlled by the owning ID.  
    h. The ID system MAY implement a name service independent of ICANN domain names.  
    i. The ID system MAY support ICANN domain names.  
    j. The ID system MAY conform to the DID standard.  
    k. The ID system SHALL be consistent with the requirements in section 8 of the [IWPS RFP](https://github.com/oma3dao/iwps-rfp/blob/main/iwps-rfp.md).  
  10. Spatial Registry  
    a. The Infrastructure addressing schedule SHALL be able to support multiple Worlds that are based in the real world (e.g. AR).  
    b. The Infrastructure MAY allow OMA3 to delegate the distribution of locations to other parties.  

## Change Log

| **Version** | **Date** | **Comments** |
| --- | --- | --- |
| 1.0 |   | First draft to public |

## Authors

- Batis Samadian (Space, OMA3)
- Alfred Tom (Wivity, OMA3)
- Mic (Africarare)
- Jerry (Animoca)
- Phillip (Identity.com)

## Appendix:  Existing Art

This appendix is a partial list of technology, practices, and solutions that are relevant to IWPS.  The goal is to add to this list so it is more comprehensive as this is a work in progress.

