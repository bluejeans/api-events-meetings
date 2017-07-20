# api-events-onvideo

BlueJeans meetings are kept up to date by and Event Service in the cloud. The meeting clients connect to this to find out what is going on in a meeting.  Various events such as who joined and left, who muted and unmuted, etc. are published by this service.

This project provides some sample code that can connect to a given meeting and receive the events.  The code uses a socket to connect to the service in order to receive the events.  A JSON payload is received when events occur.

Here is a sample event for meeting 111222333 where a guest joins.

```javascript
  "event": "statechange.endpoints.111222333",
  "meetingGuid": "",
  "props": {
    "f": [
      {
        "A1": "1",
        "A2": "0",
        "A3": "0",
        "A4": "Opus 16Khz",
        "A5": "Opus 16Khz",
        "C1": "5",
        "C5": [
          {
            "callGuid": "34c4342a-5ff5-48e6-a38f-7388f443a573",
            "capabilities": [
              "AUDIO",
              "VIDEO",
              "CONTENT"
            ],
            "connectionGuid": "connguid:4e0cffc5-9ab1-4f03-8dad-dc0df9723463",
            "endpoint": "WebRTC"
          }
        ],
        "E1": "seamguid:586e4215-a65c-42d8-9b35-d3711a4b235a",
        "L1": "1",
        "L2": "1",
        "S1": "1",
        "S2": "0",
        "T": "0",
        "V1": "1",
        "V2": "0",
        "V3": "0",
        "V4": "VP8",
        "V5": "720",
        "V6": "1280",
        "V7": "VP8",
        "V8": "180",
        "V9": "320",
        "c": "34c4342a-5ff5-48e6-a38f-7388f443a573",
        "ch": "2e9f2979f40e991e93c18137e6ca04dd",
        "e": "WebRTC",
        "lc": true,
        "m": "111222333:276818-1c55e939-6b20-427e-88cf-91c0c37e2ef8,0",
        "n": "Brandon Fuller",
        "sm": false,
        "v": "1"
      }
    ]
  }
}
```

# Usage

```
node event-service.js <partition> <numeric_meeting_id> <user_id> <access_token>
```

* Partition is something like z1, z2, etc.
* Numeric meeting ID is the end user facing ID for the meeting.
* User ID is the integer of the user attempting to connect.
* Access Token should be valid to access the meeting. You must use a password grant or meeting_passcode grant.

# Data
* m - meetingid
* n - name
* C1 - CallQuality
* L1 - Leader
* c - callguid
* e - endpoint
* T - TalkDetected
* C2 - CurrentPresenter
* S1 - SecureCall
* L2 - Layout
* S2 - SubLayout
* V1 - VideoRecv
* V2 - VideoRecvLocalMute
* V3 - VideoRecvRemoteMute
* A1 - AudioRecv
* A2 - AudioRecvLocalMute
* A3 - AudioRecvRemoteMute
* a - alerts
* A4 - AudioRecvCodec
* A5 - AudioSendCodec
* V4 - VideoRecvCodec
* V5 - VideoRecvHeight
* V6 - VideoRecvWidth
* V7 - VideoSendCodec
* V8 - VideoSendHeight
* V9 - VideoSendWidth
* C3 - ContentRecvHeight
* C4 - ContentRecvWidth      
* ch - chatEndpointGuid
* t - type
* v - visibility
* P1 - PinnedGuid
* E1 - endpointGuid
