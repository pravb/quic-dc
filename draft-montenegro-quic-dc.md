---
title: QUIC for Datacenter
abbrev: Datacenter QUIC
docname: draft-montenegro-quic-dc-latest
date: {DATE}
category: std
ipr: trust200902
area: Transport
workgroup: QUIC
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

  QUIC-TRANSPORT:
    title: "QUIC: A UDP-Based Multiplexed and Secure Transport"
    date: {DATE}
    seriesinfo:
      Internet-Draft: draft-ietf-quic-transport-latest
    author:
      -
        ins: J. Iyengar
        name: Jana Iyengar
        org: Fastly
        role: editor
      -
        ins: M. Thomson
        name: Martin Thomson
        org: Mozilla
        role: editor

  QUIC-TLS:
    title: "Using Transport Layer Security (TLS) to Secure QUIC"
    date: {DATE}
    seriesinfo:
      Internet-Draft: draft-ietf-quic-tls-latest
    author:
      -
        ins: M. Thomson
        name: Martin Thomson
        org: Mozilla
        role: editor
      -
        ins: S. Turner
        name: Sean Turner
        org: sn3rd
        role: editor


informative:


--- abstract

QUIC is a general-purpose transport for the Internet. This document defines extensions to make QUIC more
amenable to datacenter environments by allowing packet number protection to be optionally disabled.

--- note_Note_to_Readers

Discussion of this draft takes place on the QUIC working group mailing list
(quic@ietf.org), which is archived at
<https://mailarchive.ietf.org/arch/search/?email_list=quic>.

Working Group information can be found at <https://github.com/quicwg>; source
code and issues list for this draft can be found at
<https://github.com/quicwg/base-drafts/labels/-recovery>.

--- middle

# Introduction

QUIC is a new transport for the internet. In its generality, there are features which are not well suited
for datacenter environments. In particular, QUIC uses Packet Number Protection(PNP). This document defines
a negotiation using transport parameters to disable PNE. Internet facing nodes should not disable PNE, so
browsers, for example, should not implement this extension. On the other hand, properly configured nodes
within a datacenter could turn off PNE in their exchanges to avoid the CPU cost that PNE implies.

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 {{!RFC2119}} {{!RFC8174}}
when, and only when, they appear in all capitals, as shown here.

# Transport Parameter to Disable Packet Number Protection

This document defines a new transport parameter for QUIC {{QUIC-TRANSPORT}}:

disable_packet_number_protection (0x000c ?, value TBD):

: The endpoint is disabling packet number protection as specified in {{QUIC-TLS}}.
  This parameter is a zero-length value. This parameter only applies to short headers.

A peer that has sent the "disable_packet_number_protection" parameter MUST provide packet number
protection until the TLS handshake is over (thus validating the transport parameters).

# Security Considerations

TODO Security


# IANA Considerations

This document requests IANA assign a value to the new transport parameter as follows:

| Value  | Parameter Name                   | Specification                       |
|:-------|:---------------------------------|:------------------------------------|
| 0x000c | disable_packet_number_protection | This document                       |


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
