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
  RFC7641: observe
  RFC7959: blockwise
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

<!-- TODO: Maybe this reference to WoT TD can also be removed later. -->

The vocabulary and "feature-based" approach taken within this document is heavily inspired by the CoAP Protocol Binding {{WoT-CoAP-Binding}} for the W3C Web of Things (WoT), which is to be used with WoT Thing Descriptions (TDs).
Considering SDF's role as a "hub format", we aspire to be able to also take into account CoAP vocabulary when converting from and to TDs.

An important additional aspect to the base protocol-mapping specification {{-sdf-protocol-mapping}} is the fact that we rely on instance-related messages {{-sdf-instance-information}} to complement protocol information present in SDF models.
Compared to the WoT approach, we achieve a stricter separation of model and instance information this way, reducing the amount of information that needs to be supplied by a Thing itself to a minimum to enable interactions.

# Conventions and Definitions

The definitions of {{-sdf}}, {{-sdf-protocol-mapping}}, and {{-sdf-instance-information}} apply.

{::boilerplate bcp14-tagged}

# CoAP Protocol Mapping

The Constrained Application Protocol (CoAP) has been originally specified in {{-coap}}, but has since been extended via a number of specifications that features such as blockwise transfer {{-blockwise}}, the observation of resources {{-observe}}, or additional transport mechanisms {{-coap-tcp}} in addition to UDP and DTLS.

A protocol mapping for CoAP should cover these features, but should also be extensible to potential future additions to the CoAP family of standards take into account as well.

## General Considerations

CoAP can be used with three all three kinds of interaction affordances: properties, actions, and events.
The protocol mapping for an affordance will always specify the `method` as well as an `href`, which combines the URI path and potential query parameters for the resource the interaction affordance is mapped to.
To differentiate between the available transport mechanisms, a URI `scheme` (with a default value of `coap` for CoAP over TCP) can be supplied as well.

Other general qualities for CoAP include parameters for blockwise transfer, the available and accepted Content-Formats, as well as the minimal polling interval that is accepted by the respective CoAP server.
Note that since CoAP messages do not allow for the use of generic headers as HTTP does, all of these qualities map to standardized CoAP options that are registered with IANA.

In contrast to the WoT approach, the protocol binding information that is supplied via this document is targeting the _model_ level.
That means that information such as URI paths will be shared by all Thing instances that adhere to the given model.
The information that deviates between device instances, e.g., a device's `host` name or its `ipAddress`,  is provided via instance-related messages {{-sdf-instance-information}} that pass the values for the `sdfParameters` the protocol mapping defines via designated properties.
The selected `sdfProperty` definitions are indicated via JSON pointers within the `sdfParameters` map.

## Properties

TODO

## Actions

TODO

## Events

TODO

# Examples

TODO

# Security Considerations

The security considerations of {{-sdf}} as well as {{-coap}} apply to this document as well.

<!-- TODO: Add additional references/considerations. -->

# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
