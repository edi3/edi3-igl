---
title: "edi3 Inter Customs Ledger 0.1.0 Specification"
specID: "icl/1"
status: "![raw](http://rfc.unprotocols.org/spec:2/COSS/raw.svg)"
editors: "[Chris Gough](mailto:christopher.d.gough@gmail.com)"
contributors: "[Richard Spellman](https://github.com/arpentnoir)"
---

## Licence

All material published on edi3.org including all parts of this specification are the intellectual property of the UN as per the [UN/CEFACT IPR Policy](https://www.unece.org/fileadmin/DAM/cefact/cf_plenary/plenary12/ECE_TRADE_C_CEFACT_2010_20_Rev2E_UpdatedIPRpolicy.pdf).

This Specification is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version. See http://www.gnu.org/licenses.
 
## Change Process

This document is governed by the [2/COSS](http://rfc.unprotocols.org/spec:2/COSS/) (COSS).

## Language

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" 
in this document are to be interpreted as described in RFC 2119.

## Abstract

This document describes a technical specification for the trusted transfer of cross-border regulatory documents between government agencies using distributed ledger technology. The use of a distributed ledger approach for G2G document sharing offers several advantages over alternative methods.

* There is no centralised infrastructure - thereby avoiding the need for complex funding models and avoiding a single point of failure or security risk.
* Each country can host trade documents within their jurisdiction, conforming to increasingly strict data soveriegnty rules.
* Trade documents can be notarised and verified with very high integrity against tampering or forgery.
* Where appropriate (eg single use certificates), documents as digital assets can be transfered and acquitted follwing the physical asset movement.

There is no expectation that a single uber-ledger supports all G2G transactions. A apecific ledger may service as few as two countries and may be limited to a single process (eg certificates of origin) or may service multiple coujntries and multiple processes. Therefore this specification supports the use of multiple different distributed ledgers (both public and private) by defining a standrdised "Message API" that allows users within a jurisdiction to interact with multiple ledgers via a simple interface.  

This document uses Certificates of Origin as the guiding use case for the initial specification, however it is intended that the Inter Customs Ledger should be generic and allow for the transfer of any shipment related documentation between authorised agencies. 

## Glossary

Phrase | Definition
------------ | -------------
| Authorised Body| In this document, the term Authorised Body is used to denote an organisation which has authority to issue some Document. e.g. A Chamber of Commerce which issues Certificate of Origin under some FTA, a CITES Management Authority which issues CITES Permits, etc.|

| ICL | This "Intercustoms Ledger" specification |
| Node | A device on the Inter Customs Ledger network which has full visibility of the entire ledger and contriibutes to the integrity of the ledger by implementing a Consensus Algorithm |

## Glossary

To-do : replace this section with a simple link to role definitions in the dictionary specification

|Term|Description|
|----|-----------|
|3PL| Third Party Logistics Provider (eg freight forwarders)|
|Agent| Intermediaries such as customs agents|
|Carrier| A provider of transport means/equiment such a shipping line or airline|
|Certifying Body| An organisation that has been accredited to issue one or more certificate types - such as a chamber of commerce that may issue Certificates of Origin|
|Document | When capitalised in this document, this term refers to any document which gives authorisation for an importer or exporter to take some action (or be granted some further authority) with respect to an international shipment of goods. e.g. a Certificate of Origin, a Phytosanitary Certificate, an Export Declaration, etc| 
|Exporter|Business or individual that is the seller of internationally traded goods |
|ICL Node|A device on an ICL network which has full visibility of the entire ledger and contriibutes to the integrity of the ledger by implementing a Consensus Algorithm. Typically operated by a national regulator|
|ICL User|any of the above roles that interact with the ICL (typically via some software application)|
|Importer|Business or individual that is the buyer of internationally traded goods|
|Regulator| A government agnecy such as a customs authority|

## Other Projects

There have been a number of recent projects which use blockchain to implement a system which allows the validation of Certifiate of Origin issued under some Free Trade Agreement. Singapore and Kenya have both worked with industry parter vCargo Cloud to implement blockchain Certificate of Origin solutions. The first Certificate of Origin for a shipment from the UK was issued by {who?} in {month?} 2018 and in {when?} the United States were looking into the use of blockchain to validate Certificates of Origin for shipments made under {old agreements?}. These projects have highlighted the necessity for digital, blockchain based solutions to exist alongside paper based processes in the short term, requiring the continued existance of some mechanism for validating the authenticity of a paper certificate. 

Before the prevalence of distributed ledger technology, the common approach to providing for assurance as to the validity of a Document was largely achieved with the idea of a hub. There are a number of implementations of this approach which may be instructive: ICC Certificate of Origin verification website, EPIX, IPCC ePhyto hub, etc... 

The link below provides a number of resources which attempt to give an overview of the landscape of blockchain based projects related to both Certificates of Origin and International trade in general

[Survey of Blockchain Based Approaches to Managing International Trade Documentation](precedents.md)

## Introduction

International trade clearance procedures require a number of documents to be presented to satisfy the requirements of a variety of agreements. For example, in order for an importer to gain preferential tariff treatment under a Free Trade Agreement, the importer must present a valid Certificate of Origin (issued to the exporter) which states that the goods being imported qualify as originating in the country which is party to the agreement. These processes are managed largely by the transfer of paper documents which are subject to loss, alteration and forgery. 

![paper flows](DocumentFlows_AsIs.png)

In many jurisdictions, significant digitisation progress has been made for interactions between the national regulators (eg customs) and the local regulated community (eg importers, exporters, etc). In Australia for example, 99% of customs documents are already lodged electronically. However there still remains a very significant amout of paper documents that support cross border trade. The majority of the paper documents fit the same pattern; they are issued by a party in the exporting country but required by the regulator of the importing country for goods clearance. One significant reason that paper has been difficult to replace is that there is no direct trust relationshiop that allows in importing regulator to confirm the identity of the document issuer in the exporting jurisdiction. 

An Inter Customs Ledger (ICL) is proposed as an apporach to the transfer of shipment related documents between customs agencies which is immediate, permanent and irrefutable.  The intercustoms ledger is essentially a trust bridge between national identity schemes - basically the importing regulator trusts the identity of the document issuer because the exporting regulator confirms the issuer identity.  

![digital flows](DocumentFlows_ToBe.png)

The future state diagram shows the relationship between the ICL and three other key components.

* National single windows and port community systems provide a streamlined and automated means for local entities (traders, 3PL, agents, etc) to interact with their local regulators. Many nations now have some kind of single window system but implementations are varied and usually unique to the local regualatory environment. The ICL can be thought of as a cross-border integration framerwork *between* national single windows.  However, it is important that the varied and complex national rules do not bleed into the ICL so that integration remains simple. 
* National digital identity schemes are emerging in many jursdictions are provide a way for businesses and individuals in a country to prove their identity to any government agency and to any authorised non-government entity. Business identity schemes are typically linked to public tax registration numbers. Individual identities may be linked to a business identity and will normally include the idea of identity assurance levels which indicate the degree of identity integrity attached to the token holder. This means, for example, that a certificate of origin provided by an exporter to their local customs authority (possibly via a single window) can be passed to the importing authority together with a high integrity identity claim. In this way, the ICL is essentially an international "trust bridge" between national identity schemes.
* Commercial trade data platforms/pipelines are an emerging capability that seek to provide their customers with and-to-end supply chain visibility and management. They are essentially multi-source data aggregators and their scope usually includes some or all of trade, transport, financial, and regulatory data. The data managed by commerciasl pipleines is not only traditional trade documents (invoices, bills of lading etc) but also IoT streams like data feeds from instrumented smart containers. These platforms can provide significant value to their stakeholders and have a scope much larger than G2G data sharing. The ICL complements these commercial services and does not compete with them.


# High Level Requirements

## Architectural Principles

|ID|Principle|Rationale|
|--|---------|---------|
|P1|Avoid bleeding any local regulatory complexities into cross-border processes| A strong separation between local complexity and cross border document exchange is essential for scalability. The ICL specification must be as simple as possible in order for updake to scale. |
|P2|Support multiple distributed ledger types & networks|A single global uber-ledger would need to pick a technology winner, would restrict the ability to intruduce non breaking extensions, would present a high value attack target, and is unlilkely to be supported by every nation.|
|P3|Coexist nicely with paper processes|A switch from paper processes to native digital documents exchanged via ICL will not happen overnight. Therefore the ICL shoiuld add value to existing paper processes and should facilitate a simple and gradual transitoin from paper to native digital documents.|
|P4|Leverage the unique position of national regulators| Customs authorities enjoy a unique postion as the single convergence point for all imports to and exports from a country. That allows an intercustomes ledger to easily achieve complete coverage of bilateral or multilateral trading relationships.|
|P5|Complement rather than compete with commercial platforms|Regulators are not natural innovators. The ideal ICL will provide a non-comptetitive platform that leverages the position to regualators to the benefit of their constituents whilst allowing comemrcial innovation to flourish.|
|P6|Do not *require* businesses to provide more than their local regulatory obligations demand.|There may be genuine value to business in using the ICL for cross border processes beyond the regulatory minimum but regulators cannot and should not demand it. Therefore, ICL implementations should define a clear value propisition for every document that exceeds the regulatory minimum.|
|P7|Assume on-chain data is public| The ICL may be implemented on either public ledgers such as etherium or private ledgers such as hyperledger. In either case, it should be assumed that on-chain data is public since even a private ledger has multiple nodes, each of which has a has a full copy and the privacy of on-chain data cannot be guaranteed. |


## High Level Requirements

|ID|Requirement|Solution Links|
|--|-----------|--------------|
|R1|The on-chain ICL data model MUST be simple enough to support any cross border use case. |Link to ICL on-chain data model |
|R2|The on-chain ICL data SHOULD not contain sensitive or private information|link to threat-risk analysis |
|R3|A message on the ICL SHOULD provide a mechanism for discovering the full content of the document to which it relates| | |Link to discovery protocol|
|R4|Trade documents referenced by the ICL SHOULD be accessible via a consistent API|Link to Repository API|
|R5|The ICL SHOULD NOT require that the user have any knowledge of the specific leger technology used (ehterium, hyperledger, etc) |link to Message API|
|R6|The ICL SHOULD NOT assume that the user knows which ledger and which protocol to use in order to exchange a specific document type between two countries.| Link to Routing API |
|R7|Any Regulator SHOULD be able to participate in the ICL by hosting an ICL Message API that integrates with one or more ledgers| |
|R8|Participating in the network by hosting a Message API SHOULD NOT automatically grant access to the content of a document| |
|R4|The ICL MUST provide a mechanism for preventing an importer or exporter from re-using a document which is intended to have a single use| |
|R5|The ICL MUST provide some mechanism for asserting the validity of a document presented by an importer or exporter | |
|R6|The ICL MUST provide some mechanism for invalidating a Document| |
|R7|The ICL MUST provide some mechanism for specifying who can perform certain actions with respect to a Document| |

