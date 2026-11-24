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
https://w3id.org/liccium/schema/0.7.0.json
https://w3id.org/liccium/context/0.7.0.json
https://w3id.org/liccium/ont/0.3.0.ttl
```

### Schema (0.7.0)

The JSON Schema defines the structure of a Liccium declaration request payload. A declaration consists of:

- `declarationMetadata.publicMetadata` — the core ISCC-based record, including content identifiers, timestamps, declarer DID, verifiable credentials, and plugin metadata
- `declarationMetadata.optOutMetadata` — TDM-AI opt-out registry data, present when the TDM-AI plugin is active
- `declarationMetadata.faiaMetadata` — FAIA registry data, present when the FAIA plugin is active
- Cryptographic signatures (`signature`, `tsaSignature`) and optional per-plugin registry signatures

### Context (0.7.0)

The JSON-LD context maps Liccium declaration fields to RDF terms drawn from Dublin Core, schema.org, ISCC ontology, Creative Commons, IPTC, and the FAIA and Liccium ontology namespaces. It defines nested contexts for each plugin, allowing declarations to be interpreted as Linked Data.

### Changes in 0.7.0

Published versions are never edited; corrections are released as a new version. 0.7.0 corrects 0.6.0:

**Context**

- `@version` is `1.1`, as JSON-LD requires. The context version is part of the URL only.
- The `liccium`, `faia_ont` and `faia_vocab` prefixes are the namespaces (`https://w3id.org/liccium/ont/`, `https://w3id.org/faia-framework/faia_ont/`, `https://w3id.org/faia-framework/faia_vocab/`), not `.ttl` file URLs.
- The IPTC prefix is `iptc_spec`. It no longer shares its name with the `iptc` plugin key, which made the definition cyclic.
- `tdm-reservation` and `tdm-policy` map to the ontology properties of the same name.
- `faiaFlag` values resolve in the lower-case form the schema uses (`hcc`, `aac`, `aig`); the upper-case forms still resolve.
- `entryUUID` is mapped (to the same property as `entryID`).
- Credential fields (`issuer`, `validFrom`, `validUntil`, `credentialSubject`, `credentialSchema`, `proof`) are mapped, and the credentials namespace is `https://www.w3.org/2018/credentials#`.

**Schema**

- `$schema` and `@context` are pinned to the 0.7.0 URLs (0.6.0 required the 0.5.0 URLs).
- `OptOutMetadata` is defined (0.4.0 to 0.6.0 referenced it without a definition).
- `entryUUID` is the entry identifier used by the declaration API; `entryID` remains as a deprecated alias.
- A credential `issuer` is any non-empty string; a DID is recommended.

### Ontology (0.3.0 / version 1.0.0)

The OWL ontology defines the `liccium:Declaration` class and its associated data properties, including `declarerDID`, `declarationID`, `entryID`, `signature`, `tsaSignature`, `tdm-reservation`, `tdm-policy`, `supersedes`, `redirect`, and `x5cHeader`. The ontology was last modified 26 March 2026 and is published under CC BY 4.0.

---

## About

These artefacts are maintained by [Liccium B.V.](https://liccium.com) and published under the CC BY 4.0 licence. Persistent URLs are managed via [w3id.org](https://w3id.org), operated by the W3C Permanent Identifier Community Group.
