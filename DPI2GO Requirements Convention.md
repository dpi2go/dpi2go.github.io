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
| G7     | MUST       | For VoD - based assets pre-, mid- and post-roll ad insertion must work. |

## Return Path Data Reports

Digital TV playout platforms collect data from the set-top boxes of their subscribers and can pass this information on to connected advertising management platforms for performance evaluation.  

RPD is a passive measurement system. Passive means that the viewer does not have to provide any information.  He only has to watch TV via the set-top box to be measured.  The resulting number of viewers can be regarded as stable data in the sense that the same households are measured over a longer period of time.

### RPD Platform Report

The RPD Platform Report includes system-wide information in absolute figures.


| **ID** | **Status** | **Description**                                              |
| ------ | ---------- | ------------------------------------------------------------ |
| D1     | MUST       | Ad management platform must provide REST API to enable reading ad break data for all channels for a specific date via GET request.<br /><br />The requested date is passed as a parameter in the GET request.<br/><br/>Label: "day_of_interest"<br/>Format: "YYYY-MM-DD" |
| D2     | MUST       | The GET request with `date`as parameter must be answered with JSON formated array data containing:<br/><br/>- u_id: unique impression id as reference<br/>- c_id: Creative ID of the Ad<br/>- pl_id: Placement ID; must be in reference with relevant channel of requesting platform<br/>- timestamp: The GMT timestamp of the impression<br/>- duration: creative duration of the Ad in seconds |
| D3     | MUST       | Ad management platform must be able to receive a POST request to the REST API with RPD report data. |
| D4     | MUST       | The POST contains of the following JSON formated array report information for all channel for a specific date:<br/><br />- u_id: unique impression id as reference<br/>- total_unique_clients_1s: total number of unique clients who have seen min. 1 second of the ad<br/>- total_unique_clients_5s: total number of unique clients who have seen min. 5 second of the ad<br/>- total_unique_clients_50pct: total number of unique clients who have seen at least 50% of the ad<br/>- total_unique_clients_completed: total number of unique clients who have seen the complete ad<br/>- seconds_watched: total seconds watched of the spot<br/>- unique_clients_by_second: array of second level unique clients for this ad |

**Example GET:**

```
https://www.example.com/index.html?day_of_interest=2020-12-09

[
  {
    "u_id": "161362261970146604f0db586-da65-41f4-93d0-6fa437e37ec7",
    "c_id": 187014661,
    "pl_id": "whateverTV",
    "timestamp": "2020-12-09T09:33:25.0",
    "duration": 16
  },
  {
    "u_id": "161362261970146604f0db586-da65-xxxx-93d0-6fa437e37ec7",
    "c_id": 187014660,
    "pl_id": "whateverTV",
    "timestamp": "2020-12-09T09:43:25.0",
    "duration": 16
  },
  ....
]
```

**Example POST:**

```
https://www.example.com/index.html

{
  "date_report": "2020-12-09",
  "date_processing": "2020-12-12",
  "DPI_report": [
    {
      "u_id": "158362161770246604f0db586-da65-41f4-93d0-6fa437e37ec7",
      "total_unique_clients_1s": 192,
      "total_unique_clients_5s": 184,
      "total_unique_clients_50pct": 183,
      "total_unique_clients_completed": 179,
      "seconds_watched": 2923,
      "unique_clients_by_second": "182,183,182,184,183,184,183,182,182,183,182,183,183,182,183,182"
    },
    {
      "u_id": "158362161770246604f0db586-da65-xxxx-93d0-6fa437e37ec7",
      "total_unique_clients_1s": 192,
      "total_unique_clients_5s": 184,
      "total_unique_clients_50pct": 183,
      "total_unique_clients_completed": 179,
      "seconds_watched": 2923,
      "unique_clients_by_second": "182,183,182,184,183,184,183,182,182,183,182,183,183,182,183,182"
    },
    ....
  ]
}
```

## **Platform and Player SDK**   

| **ID** | **Status** | **Description**                                              |
| ------ | ---------- | ------------------------------------------------------------ |
| P1     | MUST       | Provide SDK's for Interactive Media Ads for players on different platforms, such as Android, iOS, Linux, HTML5, etc. |
| P2     | MUST       | Provide SDKs for Interactive Media Ads for DPI/DAI servers so that apps can submit a stream request for advertising and content videos - either VOD or live content - and the SDK can respond with a combined video stream. Switching between ad and content video within the application is not required. |

