---
v: 3
coding: utf-8

title: >
  Semantic Definition Format (SDF): Protocol Mapping for the Constrained Application Protocol (CoAP)
abbrev: SDF Protocol Mapping for CoAP
docname: draft-romann-asdf-coap-protocol-map-latest

category: std
submissiontype: IETF
consensus: true

area: "Applications and Real-Time"
workgroup: "A Semantic Definition Format for Data and Interactions of Things"
keyword: Internet-Draft

venue:
  group: "A Semantic Definition Format for Data and Interactions of Things"
  mail: "asdf@ietf.org"
  github: "JKRhb/sdf-coap-protocol-map"

author:
  - name: Jan Romann
    org: Universität Bremen
    email: jan.romann@uni-bremen.de

normative:
  RFC7252: coap
  RFC9880: sdf
  I-D.ietf-asdf-sdf-protocol-mapping: sdf-protocol-mapping
  I-D.ietf-asdf-instance-information: sdf-instance-information

informative:
  WoT-CoAP-Binding:
    title: Web of Things (WoT) CoAP Binding
    author:
      - name: Klaus Hartke
      - name: Jan Romann
    date: false
    target: https://w3c.github.io/wot-binding-templates/bindings/protocols/coap/index.html

...

--- abstract

This memo defines vocabulary to integrate the Constrained Application Protocol (CoAP) into Protocol Mappings {{-sdf-protocol-mapping}} for the Semantic Definition Format (SDF) for Data and Interactions of Things {{-sdf}}.

--- middle

# Introduction

This memo defines vocabulary to integrate the Constrained Application Protocol (CoAP) {{-coap}} into Protocol Mappings {{-sdf-protocol-mapping}} for the Semantic Definition Format (SDF) for Data and Interactions of Things {{-sdf}}.


# Conventions and Definitions

The definitions of {{-sdf}}, {{-sdf-protocol-mapping}}, and {{-sdf-instance-information}} apply.

{::boilerplate bcp14-tagged}

# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
