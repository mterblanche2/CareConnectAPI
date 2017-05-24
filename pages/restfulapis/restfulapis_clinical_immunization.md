---
title: Clinical | Immunization
keywords: getcarerecord, structured, rest, immunization
tags: [fhir, rest, clinical, familymemberhistory]
sidebar: accessrecord_rest_sidebar
permalink: restfulapis_clinical_immunization.html
summary: Clinical Immunization
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Immunization](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Immunization-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Immunization/[id]</div>
Return a single `Immunization` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Immunization?[searchParameters]</div>

Search for all immunization resources for a patient. Fetches a bundle of all `Immunization` resources for the specified patient.

{% include moscow.html content="[Immunization](https://www.hl7.org/fhir/DSTU2/immunization.html#search)" %}

| Name | Type | Description | SHALL | Post |
|------|------|-------------|-------|------|
| `date` | `date` | Vaccination (non)-Administration Date | Y | Immunization.date |
| `patient` | `reference` | The patient for the vaccination record | Y | 	Immunization.patient<br>(Patient) |
| `status` | `token` | Immunization event status | | Immunization.status |

<!--
| `dose-sequence` | `number` | Dose number within series |  | 	Immunization.vaccinationProtocol.doseSequence |
| `notgiven` | `token` | Administrations which were not given | | Immunization.wasNotGiven |
| `lot-number` | `string` | Vaccine Batch Number |  | Immunization.lotNumber |
| `vaccine-code` | `token` | Vaccine Product Administered |  | Immunization.vaccineCode |
-->
{% include search.date.html para="2.1." content="Immunization" %}

{% include search.patient.html para="2.2." content="Immunization" %}

{% include search.status.html para="2.3." content="Immunization" options="in-progress | on-hold | completed | entered-in-error | stopped" selected="on-hold" %}