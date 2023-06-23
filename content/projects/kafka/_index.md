---
title: Apache Kafka security advisories
description: Security information for Apache Kafka
layout: single
---

# Reporting

Do you want disclose a potential security issue for Apache Kafka? You can read more about the projects' security policy on their [security page](https://kafka.apache.org/project-security.html), and email your report to the  [Apache Kafka Security Team](mailto:security@kafka.apache.org).

# Advisories

This page is experimental: it provides consistent access to the advisories for Apache Kafka since 2023 in text and CVE JSON format. It may lag slighly behind the official CVE publications. It may also lack details found on the [project security page](https://kafka.apache.org/project-security.html).

If you have any feedback on how you would like this data to be presented, you are welcome to reach out on our public [mailinglist](/mailinglist) or privately on [security@apache.org](mailto:security@apache.org)

## Possible RCE/Denial of service attack via SASL JAAS JndiLoginModule configuration using Kafka Connect  ## { #CVE-2023-25194 }

[CVE-2023-25194](./CVE-2023-25194.cve.json)

### Affected

* Apache Kafka from 2.3.0 before 3.4.0


### Description

A possible security vulnerability has been identified in Apache Kafka Connect.<br>This requires access to a Kafka Connect worker, and the ability to create/modify connectors on it with an arbitrary Kafka client SASL JAAS config<br>and a SASL-based security protocol, which has been possible on Kafka Connect clusters since Apache Kafka 2.3.0.<br>When configuring the connector via the Kafka Connect REST API, an&nbsp;<span style="background-color: rgb(255, 255, 255);">authenticated operator</span>&nbsp;can set the <span style="background-color: rgb(255, 255, 255);">`sasl.jaas.config`<br></span>property for any of the connector's Kafka clients&nbsp;to "com.sun.security.auth.module.JndiLoginModule", which can be done via the<br>`producer.override.sasl.jaas.config`, `consumer.override.sasl.jaas.config`, or `admin.override.sasl.jaas.config` properties.<br>This will allow the server to connect to the attacker's LDAP server<br>and deserialize the LDAP response, which the attacker can use to execute java deserialization gadget chains on the Kafka connect server.<br>Attacker can cause <span style="background-color: rgb(255, 255, 255);">unrestricted deserialization of untrusted data (or)&nbsp;</span>RCE vulnerability when there are gadgets in the classpath.<br><br>Since Apache Kafka 3.0.0, users are allowed to specify these properties in connector configurations for Kafka Connect clusters running with out-of-the-box<br>configurations. Before Apache Kafka 3.0.0, users may not specify these properties unless the Kafka Connect cluster has been reconfigured with a connector<br>client override policy that permits them.<br><br>Since Apache Kafka 3.4.0, we have added a system property ("-Dorg.apache.kafka.disallowed.login.modules") to disable the problematic login modules usage<br>in SASL JAAS configuration. Also by default "com.sun.security.auth.module.JndiLoginModule" is disabled in Apache Kafka 3.4.0. <br><br>We advise the Kafka Connect users to validate connector configurations and only allow trusted JNDI configurations. Also examine connector dependencies for <br>vulnerable versions and either upgrade their connectors, upgrading that specific dependency, or removing the connectors as options for remediation. Finally,<br><span style="background-color: rgb(255, 255, 255);">in addition to leveraging the "org.apache.kafka.disallowed.login.modules" system property, Kafka Connect users can also implement their own connector<br>client config override policy, which can be used to control which Kafka client properties can be overridden directly in a connector config and which cannot.</span><br>