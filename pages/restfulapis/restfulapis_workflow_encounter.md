---
title: Workflow | Encounter
keywords: usecase, encounter
tags: [rest, fhir, workflow]
sidebar: foundations_sidebar
permalink: restfulapis_workflow_encounter.html
summary: Workflow Encounter
---
{% include search.warnbanner.html %}
{% include profile.html content="[Care Connect Encounter](http://www.interopen.org/candidate-profiles/care-connect/CareConnect-Encounter-1.html)" %}

## 1. Read ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Encounter/[id]</div>
Return a single `Encounter` for the specified id

## 2. Search Parameters ##

<div markdown="span" class="alert alert-success" role="alert">
GET /Encounter?[searchParameters]</div>

Procedure resource contains encounter information for a patient. Fetches a bundle of all `Encounter` resources for the specified patient.

{% include moscow.html content="[Encounter](https://www.hl7.org/fhir/DSTU2/encounter.html#search)" %}

| Name | Type | Description | SHALL | Path |
|------|------|-------------|-------|------|
| `date` | `date` | A date within the period the Encounter lasted | | Encounter.period |
| `patient` | `reference` | The identity of a patient to list encounters for | Y | Encounter.patient <br>(Patient) |

{% include search.date.html para="2.1." content="Encounter" %}

{% include search.patient.html para="2.2." content="Encounter" %}

## 3. Example ##

### 3.1 Query ###
Return all Organization resources with a ODS Code of C81010, the format of the response body will be xml. Replace 'baseUrl' with the actual base Url of the FHIR Server.

#### cURL ####

{% include embedcurl.html title="Search Encounter" command="curl -X GET  'http://[baseUrl]/Encounter?patient.identifier=https://fhir.nhs.uk/Id/nhs-number|9876543210&_format=xml'" %}

### 3.2 Response Headers ###

| Status Code |
|----------------|
|200 |

| Header | Value |
|-----------------|---------|
| Content-Type  | application/xml+fhir;charset=UTF-8 |

### 3.3 Response Body ###

```xml
<Bundle xmlns="http://hl7.org/fhir">
    <id value="9915a527-b22f-447d-ad02-17eb1a5203cd"/>
    <meta>
        <lastUpdated value="2017-05-24T06:37:50.061-04:00"/>
    </meta>
    <type value="searchset"/>
    <total value="1"/>
    <entry>
        <fullUrl value="http://fhirtest.uhn.ca/baseDstu2/Encounter/32445"/>
        <resource>
            <Encounter xmlns="http://hl7.org/fhir">
                <id value="32445"/>
                <meta>
                    <versionId value="1"/>
                    <lastUpdated value="2017-05-24T06:36:23.453-04:00"/>
                    <profile value="https://fhir.nhs.uk/StructureDefinition/CareConnect-Encounter-1"/>
                </meta>
                <status value="finished"/>
                <class value="outpatient"/>
                <type>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="766841000000106"/>
                        <display value="Consultation with patient encounter type (record artifact)"/>
                    </coding>
                </type>
                <patient>
                    <reference value="https://pds.proxy.nhs.uk/Patient/9876543210"/>
                </patient>
                <participant>
                    <individual>
                        <reference value="https://sds.proxy.nhs.uk/Practitioner/C5206458"/>
                        <display value="FF Nathani"/>
                    </individual>
                </participant>
                <period>
                    <start value="2017-05-24T11:34:00"/>
                    <end value="2017-05-24T11:49:00"/>
                </period>
                <reason>
                    <coding>
                        <system value="http://snomed.info/sct"/>
                        <code value="702706001"/>
                        <display value="Diabetes clinic"/>
                    </coding>
                </reason>
                <location>
                    <location>
                        <reference value="https://sds.proxy.nhs.uk/Organization/Location/RY8RK"/>
                        <display value="Long Eaton Health Clinic"/>
                    </location>
                </location>
                <serviceProvider>
                    <reference value="https://sds.proxy.nhs.uk/Organization/Organization/RY8"/>
                    <display value="Derbyshire Community Health Services NHS Foundation Trust"/>
                </serviceProvider>
            </Encounter>
        </resource>
        <search>
            <mode value="match"/>
        </search>
    </entry>
</Bundle>
```