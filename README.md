# SBT-DF203 Lab 2 — HTTP Analysis Using Wireshark

## Embedded Image Traffic Analysis

This repository contains my practical work for **SBT-DF203: Basic Networking Skills for Digital Forensics — Lab 2**.

The lab focused on analysing how a web browser retrieves a plaintext HTTP webpage containing an embedded image. I captured the traffic with TShark/Wireshark, identified the separate HTTP requests, examined TCP segmentation and reassembly, exported the transferred image from the packet capture, and verified the recovered file using SHA-256.

---

## Author

**Name:** Athanasius Orikeze Alekwe  
**Course:** Basic Networking Skills for Digital Forensics  
**Lab:** Lab 2 — HTTP Analysis Using Wireshark: Embedded Image Traffic  
**Environment:** Kali Linux 2025.3 running in VMware Workstation

---

## Lab Objectives

The practical was carried out to demonstrate how HTTP objects are transferred and reconstructed during normal browser activity.

The main objectives were to:

- Host a plaintext HTTP webpage containing an embedded image.
- Capture browser-generated HTTP traffic.
- Identify separate requests for the HTML document and embedded JPEG.
- Analyse the TCP segments carrying the image response.
- Examine the relationship between IP length, TCP payload and HTTP object size.
- Reassemble the transferred HTTP image.
- Export HTTP objects using Wireshark and TShark.
- Compare the recovered image with the original using SHA-256.
- Compare browser behaviour with curl.
- Document the effect of caching and loopback capture behaviour.

---

## Laboratory Environment

The practical was completed in an authorised local virtual environment.

| Component | Tool / Configuration |
|---|---|
| Operating System | Kali Linux 2025.3 |
| Virtualisation | VMware Workstation |
| Web Server | Apache2 |
| Browser | Firefox Private Browsing |
| Packet Analysis | Wireshark |
| Command-Line Analysis | TShark |
| HTTP Client | curl |
| Image Inspection | ImageMagick / `identify` |
| Integrity Verification | `sha256sum` and `cmp` |
| Capture Interface | Loopback (`lo`) |
| Web Server Address | `127.0.0.1:80` |

---

## Test Webpage

The Apache server hosted:

- `image.html`
- `lab_photo.jpg`

The HTML page contained an image reference similar to:

```html
<img src="lab_photo.jpg" alt="Training image">
