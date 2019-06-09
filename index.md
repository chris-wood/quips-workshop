---
layout: front
title: QUIC Privacy and Security Workshop
---

# QUIC Privacy and Security Workshop

QUIPS is a workshop focusing on QUIC security and privacy analysis efforts. Its goal is to bring this formal analysis results to the IETF working group and developer communities in order to build confidence in and improve QUIC before its widespread deployment.

## Background

The IETF QUIC protocol is a modern UDP-based, stream-multiplexing, encrypted transport protocol. Inspired by prior art, QUIC’s packet and header encryption removes cleartext  information from the network while simultaneously mitigating ossification of version-specific protocol behavior. As one example, QUIC’s standard packet header is almost fully encrypted and authenticated. To aid network operator debugging, a single (optional) bit in the header is reserved for use as a means of coarsely measuring end-to-end RTT.

The delta between TLS 1.3 (over TCP) and QUIC as secure transport protocols is non-negligible. In particular, there are several facets of the design that warrant further analysis, including, though not limited to the following:

1. Integration with cryptographic handshake. Designed with TLS 1.3 [RFC8446] as the authenticated key exchange protocol (AKE), QUIC uses state-of-the-art cryptography for establishing and using shared session secrets for packet encryption. Consequently, QUIC also benefits from extensive security analysis efforts that helped standardize TLS 1.3. However, QUIC’s modular design and the integration of TLS 1.3 in particular, has not yet received formal analysis.
2. Packet protection. Analysis of TLS assumed ordered delivery, whereas QUIC does not enjoy that benefit. The effect of packet loss on QUIC’s record layer security is important and not well understood. Moreover, QUIC's record layer provides features that TLS does not, such as header protection. Capturing the semantics of this new packet protection algorithm and proving them correct is critical.
3. Denial of Service (DoS) features. QUIC has a number of features designed to reduce the effects of DoS, both on individual connections, such as duplicate packet detection and complete packet protection, server resources, such as Retry, and the resources of bystanders, such as anti-reflection. It has yet to be shown whether or not these techniques achieve their desired goals.
4. Privacy. Many of QUIC’s features account for and attempt mitigation of packet linkability across network paths and between different connections. For example, voluntary connection migration requires endpoints to use new connection identifiers if possible as a way of preventing cross-path linkability. Also, as a means of improving endpoint privacy postures, among others, QUIC does not mandate endpoints provide any way for networks to measure per-connection Round Trip Time (RTT). The optional spin bit is the only signal made willingly available to the network. Currently, there is no strong analysis supporting the concrete privacy benefits these features provide to QUIC endpoints.

Other remaining issues include stateless reset, accepting signals from the network for PMTUD and ECN, among others.

In its current state, the QUIC draft specifications have yet to receive comprehensive security or privacy analysis. Similar to TLS 1.3, there is a limited amount of time for this analysis before the protocol is standardized. And this analysis is a critical step towards ensuring safety, correctness, security, and privacy aspects of this emerging protocol. Given this context, the goal of this workshop is to create a mechanism through which QUIC security and privacy analysis efforts can be brought to the attention of the IETF and developer communities, in order to build confidence in and improve QUIC before its widespread deployment. To that end we are seeking submissions on all aspects of the security of the QUIC protocol or implementations thereof. The goal is to present and discuss those submissions at the workshop in the presence of the designers and early implementers of QUIC and other attendees, so that the soundness of QUIC can be ascertained and any weaknesses that are identified can be mitigated or documented in a timely fashion. Note that proposals for cosmetic changes to the protocol or specification are extremely unlikely to be accepted at this stage in the process – this workshop is only aiming to find and mitigate flaws in the QUIC protocol or issues that are highly likely to affect QUIC implementations.

## Call for Submissions

We welcome submissions in the form of research papers concerning all aspects of the security and privacy of QUIC and its implementations.  Our scope is deliberately broad. It includes, by way of illustration, formal analyses of, security proofs for, and attacks on QUIC protocol abstractions, analysis of components of the overall protocol suite, and positive and negative results concerning the security of specific implementations.  Submissions will be evaluated on their relevance to the workshop objective of building confidence in and improving QUIC.

Papers already published, scheduled for publication, or intended for submission elsewhere are welcome as submissions.  The workshop will not have a formal proceedings, though we expect speakers to allow us to make their presentations available for free on the workshop website during and after the workshop.  Our intention is that this should not prejudice authors’ ability to publish their work in other, more formal venues before or after the workshop.  Authors of accepted submissions are also strongly encouraged to make their papers available to the community as preprints through the usual channels.

Submissions should be non-anonymous, and consist of a main body and well-marked appendices. For papers that have already been published or accepted for publication already, submission should include a cover letter (at most 2 pages) commenting on what the workshop presentation would contain, appended with the accepted/published paper. For papers not already formally published, the main body should be at most 12 pages in length, in single-column format, with reasonable margins and fonts. If a work is currently in submission to a different venue, please note this in your submission. Such works will not be considered “double submissions”, and are welcome at this workshop. Appendices are unlimited in length; however, Workshop Technical Programme Committee members may base their decisions solely on the contents of the main bodies of submissions.

## See Also

* [TLS 1.3 -- Ready or Not](https://www.ndss-symposium.org/ndss2016/tron-workshop-programme/)

----
