# Mediroza General Hospital — Consolidated Penetration Testing Report

> **Assessment Type:** Black-Box Penetration Testing Project (Consolidated Evidence Review)  
> **Target:** `https://medirozahospital.com` (Target domain only)  
> **Engagement / Cohort:** Networkwalks Batch B083 — Week 4  
> **Review Date:** 24 November 2026  
> **Prepared By:** Kavan Joshi  
> **Environment:** Kali Linux  

---

## ⚠️ Confidentiality & Scope Notice

This repository contains documentation for an **authorised educational penetration-testing project** under the Networkwalks project brief[cite: 1]. 

* **Scope:** Restricted strictly to `https://medirozahospital.com` (five-day project window in brief)[cite: 1, 3].
* **Rules of Engagement:** No social engineering, no denial-of-service (DoS) activity, and no out-of-scope testing[cite: 1, 3].
* **Data Handling:** Sensitive patient, employee, shareholder, credential, or other confidential records must not be published or distributed in an uncontrolled manner[cite: 1, 4, 6].

---

## 📋 Executive Summary & Evidence Qualification

This consolidated report organizes and qualifies the evidence available across project milestones (**M1–M4**) through **24 November 2026**[cite: 1, 2, 3]. Rather than treating unverified or incomplete artifacts as confirmed findings, each item is strictly qualified against primary evidence[cite: 2]:

* **M2 File Integrity & Encryption:** Three locked PDF files were associated with M2 analysis with SHA-256 verification reported as `OK` and PDF encryption metadata identified as **PDF 1.6 / Standard V4.4 / AESv2 / revision 4 / 128-bit**[cite: 3, 4]. However, a matching SHA-256 hash or encryption metadata alone does not prove successful decryption or plaintext recovery[cite: 4].
* **M3 Public Reconnaissance:** A reconnaissance record dated **24 November 2026** documents passive/public observations—including DNS records, SPF/DMARC/CAA/AAAA queries, HTTP/2 response headers, LiteSpeed server disclosure, TLS certificate details, `robots.txt`, `security.txt`, `sitemap.xml`, HTML/CMS metadata, and six security headers not observed on the inspected homepage response—with **no exploitation performed**[cite: 3, 4, 5].
* **Outstanding Evidence:** Primary proof for **M1** initial access/retrieval, **M2** recovered plaintext contents, and the original **M3** employee salary and shareholder data-exposure objective were not present in the reviewed evidence[cite: 2, 3, 4]. Accordingly, no confirmed exploitable vulnerability or overall risk rating is asserted until missing evidence is validated[cite: 3, 5, 7].

---

## 🗂️ Milestone Status Overview

| Workstream | Documented Status | Evidence Position |
| :--- | :--- | :--- |
| **M1 – Initial Access** | Not independently verified[cite: 3] | Three PDFs were later referenced in M2; access route, request/response captures, timestamps, and proof screenshots were not available[cite: 3, 4]. |
| **M2 – Data Extraction / Encryption** | Partially evidenced[cite: 3] | Three PDF SHA-256 digests and encryption metadata recorded; successful plaintext recovery not established[cite: 3, 4]. |
| **M3 – Original Data-Exposure Task** | Not evidenced[cite: 3] | No verified employee salary or shareholder exposure evidence supplied in reviewed records[cite: 3, 4]. |
| **M3 – Public Reconnaissance** | Documented[cite: 3] | Reconnaissance report dated 24 November 2026 available; passive public inspection only (no exploitation)[cite: 3, 4]. |
| **M4 – Reporting** | Prepared[cite: 3] | Consolidated report structured per M4 guidelines, documenting findings, gaps, and remediation guidance[cite: 2, 3]. |

---

## 🔍 Key Observations Summary (M2 & M3)

> Observations below reflect available M2 and M3 records and provisional review priorities—not confirmed vulnerabilities or validated exploits[cite: 4, 5].

* **PDF Integrity & Encryption (`F-01`, `F-02`):** SHA-256 digests recorded for three PDFs (`PDF 1`, `PDF 2`, `PDF 3`)[cite: 4, 8]; metadata indicates **PDF 1.6**, **Standard V4.4**, **AESv2**, **revision 4**, **128-bit**[cite: 4, 8].
* **DNS & Email Posture (`F-03`, `F-04`, `F-05`):** A record `199.188.201.16`, three MX records (`mx1-hosting.jellyfish.systems`, `mx2-hosting.jellyfish.systems`, `mx3-hosting.jellyfish.systems`), Namecheap nameservers, SPF policy, and DMARC `v=DMARC1; p=none;` observed; no `AAAA` or `CAA` answer returned for queried names[cite: 4, 5].
* **Web Server & TLS (`F-06`, `F-07`):** HTTP/2 (`200 OK`) response with `Server: LiteSpeed` and `X-Turbo-Charged-By: LiteSpeed`; TLS certificate issued to `CN=medirozahospital.com` by `SSL.com TLS Issuing RSA CA R1` (valid `14 Aug 2026 – 28 Feb 2027`)[cite: 4, 5].
* **Discovery & Metadata (`F-08` – `F-11`):** `robots.txt` (`200`) listed `/patient/`, `/staff/`, and `/old/` as disallowed; `security.txt` returned `404`; `sitemap.xml` (`200`) listed `index.html`, `about.html`, `doctors.html`, and `contact.html`; homepage metadata noted `Mediroza CMS 1.4.2`[cite: 4, 5].
* **Response Security Headers (`F-12`):** `Strict-Transport-Security` (HSTS), `Content-Security-Policy` (CSP), `X-Frame-Options`, `X-Content-Type-Options`, `Referrer-Policy`, and `Permissions-Policy` were not observed in the inspected homepage response[cite: 5].

---

## 🛠️ Tools & Environment Evidenced

* **OS:** Kali Linux[cite: 3]
* **Utilities:** `OpenSSL s_client` (TLS certificate inspection), `curl` (HTTP headers & discovery-file checks), SHA-256 hashing utilities, and PDF encryption/metadata inspection[cite: 3, 4]

---

## 🛡️ High-Level Remediation Priorities

* **Access Controls & Sensitive Files:** Enforce strict server-side authentication and authorization on all document/report endpoints; never rely on `robots.txt` or client-side/PDF passwords alone for access control[cite: 5, 6].
* **Email Authentication:** Monitor DMARC aggregate reports (`p=none`) and validate all legitimate senders before transitioning toward enforcement (`quarantine` or `reject`)[cite: 5, 6].
* **Web & Transport Hardening:** Test and deploy relevant HTTP security headers across pages, redirects, and subdomains; validate TLS configuration/chains and minimize unnecessary version disclosures[cite: 6].
* **Evidence & Chain of Custody:** Retain reproducible request/response proof, redacted decryption evidence, and verified file hashes for every milestone claimed[cite: 6].

---

## 📁 Repository Contents

* `Mediroza_Consolidated_Penetration_Testing_Report.pdf` — Consolidated assessment report covering Executive Summary, Scope & Methodology, Milestone Activity Summary, Findings & Supporting Evidence, Risk Rating, Recommendations & Remediation, Limitations & Outstanding Evidence, Conclusion, and Appendices A–B[cite: 2].
