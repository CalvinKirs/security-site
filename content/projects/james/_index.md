---
title: Apache James security advisories
description: Security information for Apache James
layout: single
---

# Reporting

Do you want disclose a potential security issue for Apache James? Send your report to the  [Apache Security Team](mailto:security@apache.org).

# Advisories

This page is experimental: it provides consistent access to the advisories for Apache James since 2023 in text and CVE JSON format. It may lag slighly behind the official CVE publications. 

If you have any feedback on how you would like this data to be presented, you are welcome to reach out on our public [mailinglist](/mailinglist) or privately on [security@apache.org](mailto:security@apache.org)

## Temporary File Information Disclosure ## { #CVE-2022-45935 }

[CVE-2022-45935](./CVE-2022-45935.cve.json)

### Affected

* Apache James server through 3.7.2


### Description

Usage of temporary files with insecure permissions by the Apache James server allows an attacker with local access to access private user data in transit. <br><br>Vulnerable components includes the SMTP stack and IMAP APPEND command.<br><br>This issue affects Apache James server version 3.7.2 and prior versions.

## Temporary File Information Disclosure in MIME4J TempFileStorageProvider ## { #CVE-2022-45787 }

[CVE-2022-45787](./CVE-2022-45787.cve.json)

### Affected

* Apache James MIME4J through 0.8.8


### Description

Unproper laxist permissions on the temporary files used by MIME4J TempFileStorageProvider may lead to information disclosure to other local users. This issue affects Apache James MIME4J version 0.8.8 and prior versions.<br><br>We recommend users to upgrade to MIME4j version 0.8.9 or later.<br>

## Privilege escalation through unauthenticated JMX ## { #CVE-2023-26269 }

[CVE-2023-26269](./CVE-2023-26269.cve.json)

### Affected

* Apache James server through 3.7.3


### Description

<div>Apache James server version 3.7.3 and earlier provides a JMX management service without authentication by default. This allows privilege escalation by a 
malicious local user.</div><div>Administrators are advised to disable JMX, or set up a JMX password.</div><div>Note that version 3.7.4 onward will set up a JMX password automatically for Guice users.<br></div>