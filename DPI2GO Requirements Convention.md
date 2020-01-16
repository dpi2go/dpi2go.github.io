# DPI2GO Requirements Convention

## Revision History

| **Date**   | **Revision** | **Description**                                        |
| ---------- | ------------ | ------------------------------------------------------ |
| 2020-01-15 | Rev 1.0      | Initial Version of the Requirement Convention Document |

## Requirement types

| **Status** | **Description**                                             |
| ---------- | ----------------------------------------------------------- |
| MUST       | Mandatory requirement.                                      |
| SHOULD     | Requirement which should be met, but which is not absolute. |
| CAN        | Optional requirement which will strengthen the offering.    |

_Note: Please keep in mind that the current SHOULD &amp; CAN requirements may already become MUST in the course of the next tender._

# Minimum functional requirements for the DPI/DAI components

## Core requirements

| **ID** | **Status** | **Description**                                              |
| ------ | ---------- | ------------------------------------------------------------ |
| G1     | MUST       | Processing of redundant DVB-compliant multicast transport streams (mostly satellite-based and based on this in dynamic bandwidth characteristics ...), which are equipped with SCTE35 markers for the respective channel. |
| G2     | MUST       | Correct processing of all possible different SCTE35 configurations and applications by the content / channel operators in question. |
| G3     | MUST       | The maximum additional latency in the live transport stream (TS) must not exceed 1 second. |
| G4     | MUST       | The output TS of the DPI server, as the new "master TS", must correspond to the input TS quality and ensure that the subsequent transcoder can process all further signal formats for IPTV (incl. up/down scaling) and OTT profiles without interference. |
| G5     | MUST       | The digital video formats to be supported are: UHD/HD/SD.    |
| G6     | MUST       | The DPI/DAI service components must provide all the non-proprietary interfaces commonly used in the media industry for connecting external ad management systems, but in any case they must provide the latest versions of VAST/VMAP. |

## Return Path Data Reports

| **ID** | **Status** | **Description** |
| ------ | ---------- | --------------- |
| D1     | MUST       |                 |
|        |            |                 |



## **Platform and Player SDK**   

| **ID** | **Status** | **Description** |
| ------ | ---------- | --------------- |
| P1     | MUST       |                 |
|        |            |                 |


