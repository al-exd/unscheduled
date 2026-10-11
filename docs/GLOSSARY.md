# Glossary

The shared vocabulary of the project. Code, tests, and documentation use these terms with these meanings.

## External terms

**CVE (Common Vulnerabilities and Exposures)**
A publicly known vulnerability, identified by an ID such as `CVE-2026-12345`. Every CVE has a short text description and a list of references.

**CVE Program**
The program that assigns CVE IDs and publishes the authoritative list of CVE records.

**CNA (CVE Numbering Authority)**
An organization allowed to assign CVE IDs and publish CVE records, usually the vendor or a security researcher's organization. Some CNAs include their own structured data, but many do not.

**NVD (National Vulnerability Database)**
The NIST database that republishes CVEs and adds structured data to them: affected products, weakness types and severity scores. It no longer analyzes every CVE.

**NVD status**
The processing state the NVD assigns to a CVE: `Received`, `Awaiting Analysis`, `Undergoing Analysis`, `Analyzed`, `Modified`, `Deferred`, or `Rejected`.

**KEV (Known Exploited Vulnerabilities)**
The CISA catalog of CVEs known to be exploited in the wild.

**OSV (Open Source Vulnerabilities)**
A database of vulnerabilities in open-source packages, with affected package versions. Many of its entries map to CVEs.

**EPSS (Exploit Prediction Scoring System)**
A daily estimate of the probability that a CVE will be exploited in the next 30 days.

**CVSS (Common Vulnerability Scoring System)**
A standard for scoring the severity of a vulnerability from 0.0 to 10.0. Several versions exist, and different sources may give different scores for the same CVE.

**CPE (Common Platform Enumeration)**
A standard name for a product, for example `cpe:2.3:a:apache:http_server:2.4.58:*:*:*:*:*:*:*`.

**CWE (Common Weakness Enumeration)**
A catalog of weakness types, for example `CWE-79` (cross-site scripting).

**Reference**
A URL attached to a CVE, such as a vendor advisory, a patch, or a bug report. References are untrusted input.

## Domain terms

**Source**
A public database the project imports CVE data from. Each source has its own format, update rhythm and coverage.

**Raw record**
The data exactly as a source published it. It is kept so that the cleaned data can always be rebuilt.

**Consolidated record**
The single view of a CVE built from the raw records of every source that knows it.

**Provenance**
The source a piece of data came from. Every field of a consolidated record keeps its provenance.

**Disagreement**
Two sources giving different values for the same field of the same CVE, for example two different severity scores.

**Coverage**
The share of CVEs a source knows about, and how complete its data is for them.

**Analyzed CVE**
A CVE that has received structured data (affected products, weakness type, severity) from an analyzing source such as the NVD.

**Unanalyzed CVE**
A CVE without that structured data.

**Analysis delay**
The time between a CVE's publication and its analysis by a given source.

**Rejected CVE**
A CVE ID withdrawn by the CVE Program. It stays in the data, marked as rejected.

**Affected product**
A vendor and product that a CVE impacts.

**Version range**
The versions of an affected product that are vulnerable. Each bound is either inclusive or exclusive and may be open, for example "from 2.0 inclusive up to 2.4.59 exclusive".

**Weakness type**
The kind of flaw behind a CVE, expressed as a CWE.

**Severity**
How serious a CVE is, expressed as a CVSS score and its level (low, medium, high, critical).

**Known exploitation**
Whether a CVE is listed as exploited in the wild, for example in the KEV catalog.

**Filter**
A condition that selects a subset of CVEs, such as a date range, a severity level or a source.

**Statistic**
A measure computed over a set of CVEs, with an exact and documented definition, for example "share of CVEs published this month that are unanalyzed".

## Domain events

**CVE imported**
A CVE not known before has been stored by ingestion.

**CVE updated**
A source has published a change to a CVE already stored.

**Sources disagree**
Consolidation has found a disagreement between two sources on the same CVE.

## Later phase: AI suggestions

**AI suggestion**
Data proposed by a language model for an incomplete CVE. It is never presented as official data, and it records its source model, prompt version, confidence and sources.

**Evaluation**
Measuring AI suggestions against CVEs that already have official data, without showing the model the answer. Accuracy is measured per field, per model and per prompt version.

## Open questions

- Which NVD statuses count as *analyzed*? `Modified` CVEs have usually been analyzed before. `Deferred` CVEs will likely never be analyzed.
- Does structured data provided by a CNA count as analysis?
- When sources disagree, does the consolidated record pick a preferred value, or only show every value?
- Which sources are part of the MVP, and in which order are they added?
