---
title: Apache BookKeeper security advisories
description: Security information for Apache BookKeeper
layout: single
---

# Reporting

Do you want disclose a potential security issue for Apache BookKeeper? Send your report to the  [Apache Security Team](mailto:security@apache.org).

# Advisories

This page is experimental: it provides consistent access to the advisories for Apache BookKeeper since 2023 in text and CVE JSON format. It may lag slighly behind the official CVE publications. 

If you have any feedback on how you would like this data to be presented, you are welcome to reach out on our public [mailinglist](/mailinglist) or privately on [security@apache.org](mailto:security@apache.org)

## Java Client Uses Connection to Host that Failed Hostname Verification ## { #CVE-2022-32531 }

[CVE-2022-32531](./CVE-2022-32531.cve.json)

### Affected

* Apache BookKeeper through 4.14.5
* Apache BookKeeper at 4.15.0


### Description

<span style="background-color: rgb(255, 255, 255);">The Apache Bookkeeper Java Client (before 4.14.6 and also 4.15.0) does not close the connection to the</span><span style="background-color: rgb(255, 255, 255);"> bookkeeper server when TLS hostname verification fails. This leaves</span><br><span style="background-color: rgb(255, 255, 255);">the bookkeeper client vulnerable to a man in the middle attack.<br></span><br>The problem affects BookKeeper client prior to versions 4.14.6 and 4.15.1.