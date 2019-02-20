---
title: "edi3 Inter Customs Ledger 0.1.0 Specification"
specID: "icl/1"
status: "![raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)"
editors: "[Richard Spellman](https://github.com/arpentnoir)"
contributors: 
---

## Introduction
International trade clearance procedures require a number of documents to be presented to satisfy the requirements of a variety of agreements. For example, in order for an importer to gain preferential tariff treatment under a Free Trade Agreement, the importer must present a valid Certificate of Origin (issued to the exporter) which states that the goods being imported qualify as originating in the country which is party to the agreement. These processes are managed largely by the transfer of paper documents which are subject to loss, alteration and forgery. 
> FIXME
there should be some text here describing the financial consequences of the last statement above


> FIXME
clear and consise description of the problem that an ICL proposes to solve
e.g. Clearance of shipments can be delayed because of uncertainty around accompanying documentation, causing signifant costs to bla bla bla

An Inter Customs Ledger is proposed as an apporach to the transfer of shipment related documents between customs agencies which is immediate, permanent and irrefutable.

This document uses the case of managing a Certificate of Origin as the guiding use case for the initial specification, however it is intended that the Inter Customs Ledger should be generic and allow for the transfer of any shipment related documentation between authorised agencies. 

#### Background
The following present some existing approaches to implementing a blockchain solution to managing certificates of origin, as well as some general trade related blockchain initiatives, and non-blockchain related solutions to solving some of the problems of international shipment documentation. 

> FIXME
put brief summary of existing certificate of origin solutions and a couple of other things here. short paragraph. reference link below

[Survey of Blockchain Based Approaches to Managing International Trade Documentation](precedents.md)

#### Users
> FIXME
list of parties and their roles etc
exporter - applies for certificate
authorised body - issues certificate
importer - applies for preferential tariff treatment
customs authority - grants preferential tariff treatment


#### Example Scenarios
> FIXME
> Get full list of documents required for a simple case where only additional 
> documentation beyond generic shipment documentation is a Certificate of Origin
> maybe a wine shipment? 
> as well as all documents required for a more complex scenario, maybe orchids (certificate of origin, CITES, phytosanitary...) as well as full list of parties involved

#### Open Questions
**What is the relationship between a party running a node and a party authorised to view the contents of a Document?**
This goes to the question of what content of a given document is available on-chain. Some options are: 

> FIXME
> elaborate on each of the options below 
- all document content is on-chain and encrypted
- document content is published and only a reference to the document and it's hash is on-chain
- all document content is on chain and not encrypted (being a node is the same as having authority to view document details)

**Should an Inter Customs Ledger manage the state lifecyle of a Document?**

**What is a Document in the context of the Inter Customs Ledger?**
  - a thing added to the chain by an authorised body which has state and allows some party to take some action dependant on that state
  - a digital asset granted to a party that allows that party to trade the asset for some service

**What is the appropriate 'chain of custody' of a document in the context of the Inter Customs Ledger?**
  - export customs to import customs
  - authorised body to exporter to importer to import customs

**How should the ICL function in the context of an existing legislated paper based process?**


## Design Goals

**Avoid proliferation of ledgers**
> FIXME
i.e. reduce burdon on parties wishing to join network

**Maintain privacy of document content**
> FIXME
i.e. a node on the network may not be authorised to view the content of a document

**Collect meaningful data about the use of a Document**
> FIXME
i.e. some state management to prevent double spend and track documents etc


## Future Directions
> FIXME
increate breadth and depth with interledger protocols


These paper documents are inherently prone to loss, alteration and forgery. The aim of the Inter Customs Ledger is to provide a mechanism which allows interested parties to determine the validity of a given shipment document. 


## Status

This document is currently focussed toward providing enough background content to inform discussions on elaborating the design of an Inter Customs Ledger. 


## Glossary

Phrase | Definition
------------ | -------------
| Document | | 
| Clearance| |
| Authorised Body| |
| Node | |


This service depends on - TBA.

The TBA specification depends on this document. Note, TBA.
 
## Licence

Copyright (c) 2018 the Editor and Contributors. All rights reserved.

This Specification is free software; you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software Foundation; 
either version 3 of the License, or (at your option) any later version.

This Specification is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR
PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program;
if not, see [http://www.gnu.org/licenses](http://www.gnu.org/licenses).

 
## Change Process

 This document is governed by the [2/COSS](http://rfc.unprotocols.org/spec:2/COSS/) (COSS).

## Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" 
in this document are to be interpreted as described in RFC 2119.

# High Level Requirements
1. Any Customs Authority SHOULD be able to participate in the ICL by running a Node
2. Participating in the network by running a Node SHOULD NOT grant access to the content of a document
3. A message on the Inter Customs Ledger MAY provide a mechanism for discovering the full content of the document to which it relates
4. The Inter Customs Ledger MUST provide a mechanism for preventing an importer or exporter from re-using a document which is intended to have a single use
5. The Inter Customs Ledger MUST provide some mechanism for asserting the validity of a document presented by an importer or exporter 
6. The Inter Customs Ledger MUST provide some mechanism for invalidating a Document
7. The Inter Customs Ledger MUST provide some mechanism for specifying who can perform certain actions with respect to a Document


## State Lifecycle
