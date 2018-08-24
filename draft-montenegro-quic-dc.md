---
title: QUIC for Datacenter
abbrev: Datacenter QUIC
docname: draft-montenegro-quic-dc-latest
category: info

ipr: trust200902
area: General
workgroup: QUIC Working Group
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: G. Montenegro
    name: Gabriel Montenegro
    organization: Microsoft Corporation
    email: Gabriel.Montenegro@Microsoft.com

normative:
  RFC2119:

informative:



--- abstract

QUIC is a general-purpose transport for the Internet. This document defines extensions to make QUIC more
amenable to datacenter environments by allowing packet number encryption to be optionally disabled.

--- middle

# Introduction

QUIC is a new transport for the internet. In its generality, there are features which are not well suited
for datacenter environments. In particular, QUIC uses Packet Number Encryption (PNE). This document defines
a negotiation using transport parameters to disable PNE. Internet facing nodes should not disable PNE, so
browsers, for example, should not implement this extension. On the other hand, properly configured nodes
within a datacenter could turn off PNE in their exchanges to avoid the CPU cost that PNE implies.

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 {{RFC2119}} {{!RFC8174}}
when, and only when, they appear in all capitals, as shown here.

# Transport Parameter to Disable Packet Number Encryption

TODO
TEST


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
