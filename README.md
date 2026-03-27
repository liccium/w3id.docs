# Liccium and FAIA: Schema, Context, Ontology & Vocabulary

Versioned JSON Schema, JSON-LD context, OWL ontology, and vocabulary definitions for Liccium metadata declarations and the FAIA (Fair AI Attribution) framework.

This repository contains two distinct but related sets of semantic artefacts, served via persistent w3id.org URLs.

---

## Liccium

Liccium is a content declaration infrastructure built on the International Standard Content Code (ISCC, ISO 24138:2024). It provides a framework for creators and rightsholders to make cryptographically signed, timestamped declarations about their digital content, linking persistent identifiers to verifiable identity and machine-readable rights metadata.

### Folders

`schema/` — JSON Schema files for validating Liccium declaration payloads

`context/` — JSON-LD context files mapping Liccium fields to RDF terms

`ont/` — OWL ontology files defining Liccium classes and properties in Turtle serialisation

### Persistent URLs

Reference the latest published versions via their w3id.org persistent identifiers:

```
https://w3id.org/liccium/schema/0.4.0.json
https://w3id.org/liccium/context/0.4.0.json
https://w3id.org/liccium/ont/0.3.0.ttl
```

### Schema (0.4.0)

The JSON Schema defines the structure of a Liccium declaration request payload. A declaration consists of:

- `declarationMetadata.publicMetadata` — the core ISCC-based record, including content identifiers, timestamps, declarer DID, verifiable credentials, and plugin metadata
- `declarationMetadata.optOutMetadata` — TDM-AI opt-out registry data, present when the TDM-AI plugin is active
- `declarationMetadata.faiaMetadata` — FAIA registry data, present when the FAIA plugin is active
- Cryptographic signatures (`signature`, `tsaSignature`) and optional per-plugin registry signatures

### Context (0.4.0)

The JSON-LD context maps Liccium declaration fields to RDF terms drawn from Dublin Core, schema.org, ISCC ontology, Creative Commons, IPTC, and the FAIA and Liccium ontology namespaces. It defines nested contexts for each plugin, allowing declarations to be interpreted as Linked Data.

### Ontology (0.3.0 / version 1.0.0)

The OWL ontology defines the `liccium:Declaration` class and its associated data properties, including `declarerDID`, `declarationID`, `entryID`, `signature`, `tsaSignature`, `tdm-reservation`, `tdm-policy`, `supersedes`, `redirect`, and `x5cHeader`. The ontology was last modified 26 March 2026 and is published under CC BY 4.0.

---

## FAIA

FAIA (Fair AI Attribution) is a plugin and federated declaration registry built on Liccium's core infrastructure. It extends the Liccium framework with a dedicated vocabulary and ontology for disclosing AI involvement in content creation, enabling machine-readable, cryptographically verifiable attribution of AI-assisted or AI-generated content.

FAIA is designed to support regulatory compliance with AI transparency requirements (including the EU AI Act and equivalent legislation) and to enable systematic identification of synthetic content for AI training data governance.

### Folder

`faia/` — OWL ontology and vocabulary files for the FAIA framework in Turtle and JSON-LD serialisations

### Persistent URLs

```
https://w3id.org/liccium/faia/ont/0.4.0.ttl
https://w3id.org/liccium/faia/vocab/0.4.0.ttl
```

### Vocabulary

The FAIA vocabulary covers three layers of AI involvement disclosure:

**FAIA Flags** signal the overall level of AI involvement at the content level:

- `hcc` — Human-Created Content: no AI involvement at any stage of creation or editing
- `aac` — AI-Assisted Content: human remains primary creator; AI contributed during the process
- `aig` — AI-Generated Content: AI is the primary creative agent; human input limited to prompting or selection

**Activity Codes** describe the specific operation performed, using either established domain vocabularies (STM AI Classification for academic manuscripts, IPTC Digital Source Type for visual media) or FAIA's own generic, media-independent codes: `coCreation`, `contribution`, `enhancement`, `refinement`, `transformation`, `analysis`.

**System Attribution** identifies the specific AI system used, via two fields:

- `systemAttribution` — the entity operating the AI system, e.g. `Anthropic`
- `systemVersion` — the specific version of the AI system used, e.g. `Claude Sonnet 4.6`

### Ontology namespace

The FAIA ontology is published at `https://w3id.org/liccium/faia/ont/` and defines terms including `faia:CreationMetadata`, `faia:RegistryMetadata`, `faia:flag`, `faia:activityCode`, `faia:systemAttribution`, `faia:systemVersion`, and `faia:preferences`.

---

## About

These artefacts are maintained by [Liccium B.V.](https://liccium.com) and published under the CC BY 4.0 licence. Persistent URLs are managed via [w3id.org](https://w3id.org), operated by the W3C Permanent Identifier Community Group.

For more information:

- Liccium: [https://liccium.com](https://liccium.com)
- FAIA documentation: [https://faia.liccium.com](https://faia.liccium.com)
- FAIA registry: [https://faia.io](https://faia.io)
- ISCC standard: [https://schema.iscc.codes](https://schema.iscc.codes)
