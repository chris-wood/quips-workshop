---
layout: front
title: QUIPS
---

# QUIC Privacy and Security Workshop

QUIPS is a workshop focusing on QUIC security and privacy analysis efforts. Its goal is to bring formal analysis results to the IETF working group and developer communities in order to build confidence in and improve QUIC before its widespread deployment.

## Background

The IETF QUIC protocol is a modern UDP-based, stream-multiplexing, encrypted transport protocol. Inspired by prior art, QUIC’s packet and header encryption removes cleartext  information from the network while simultaneously mitigating ossification of version-specific protocol behavior. As one example, QUIC’s standard packet header is almost fully encrypted and authenticated. To aid network operator debugging, a single (optional) bit in the header is reserved for use as a means of coarsely measuring end-to-end RTT.

The delta between TLS 1.3 (over TCP) and QUIC as secure transport protocols is non-negligible. In particular, there are several facets of the design that warrant further analysis, including, though not limited to the following:

1. *Integration with the TLS 1.3 handshake.*: QUIC is designed to re-use the TLS 1.3 [RFC8446] authenticated key exchange protocol that produces the traffic secrets used to encrypt QUIC packets. While the TLS 1.3 key exchange protocol has received extensive formal analysis effort during its standardization, QUIC’s modular use of the TLS handshake to generate secrets and authenticate negotiated transport parameters has not received as much attention. Some of the properties of TLS 1.3, such as the authentication by the handshake of the termination of 0-RTT data by the "end of early data" message, rely on assumptions that hold for the TLS record layer, but not for the QUIC record layer.
2. *Packet protection*: analysis of TLS assume reliable, ordered delivery of network messages, which does not hold in QUIC. The effect of packet loss on QUIC’s record layer security is important and not well understood. Moreover, QUIC's record layer provides features that TLS does not, such as header protection. Capturing the semantics of this new packet protection algorithm and proving them correct is critical.
3. *Denial of Service (DoS) features*: QUIC has a number of features designed to reduce the effects of DoS, both on individual connections, such as duplicate packet detection and complete packet protection, server resources, such as Retry, and the resources of bystanders, such as anti-reflection. It has yet to be shown whether or not these techniques achieve their desired goals.
4. *Privacy*: many of QUIC’s new features account for and attempt to mitigate the linkability of packets to users across network paths and between connections. For example, voluntary connection migration requires endpoints to use new connection identifiers if possible as a way of preventing cross-path linkability. Also, as a means of improving endpoint privacy postures, among others, QUIC does not mandate endpoints provide any way for networks to measure per-connection Round Trip Time (RTT). The optional spin bit is the only signal made willingly available to the network. Currently, there is no strong analysis supporting the concrete privacy benefits these features provide to QUIC endpoints.
5. *Application security*: while TLS exposes a socket-based send/recv interface, QUIC integrates most of the dynamic stream multiplexing interface from HTTP/2. Applications must target this new interface, leading to new protocols such as HTTP/3. The security implications of the new transport interface for legacy and new applications not well studied. For instance, it is unclear how an application can tell apart which parts of incoming messages have been protected with the 0-RTT or the 1-RTT secret. 

Other remaining issues include stateless reset, accepting signals from the network for PMTUD and ECN, among others.

In its current state, the QUIC draft specifications have yet to receive comprehensive security or privacy analysis. Similar to TLS 1.3, there is a limited amount of time for this analysis before the protocol is standardized. And this analysis is a critical step towards ensuring safety, correctness, security, and privacy aspects of this emerging protocol. Given this context, the goal of this workshop is to create a mechanism through which QUIC security and privacy analysis efforts can be brought to the attention of the IETF and developer communities, in order to build confidence in and improve QUIC before its widespread deployment. To that end we are seeking submissions on all aspects of the security of the QUIC protocol or implementations thereof. The goal is to present and discuss those submissions at the workshop in the presence of the designers and early implementers of QUIC and other attendees, so that the soundness of QUIC can be ascertained and any weaknesses that are identified can be mitigated or documented in a timely fashion. Note that proposals for cosmetic changes to the protocol or specification are extremely unlikely to be accepted at this stage in the process – this workshop is only aiming to find and mitigate flaws in the QUIC protocol or issues that are highly likely to affect QUIC implementations.

## Call for Submissions

We welcome submissions in the form of research papers concerning all aspects of the security and privacy of QUIC and its implementations.  Our scope is deliberately broad. It includes, by way of illustration, formal analyses of, security proofs for, and attacks on QUIC protocol abstractions, analysis of components of the overall protocol suite, and positive and negative results concerning the security of specific implementations.  Submissions will be evaluated on their relevance to the workshop objective of building confidence in and improving QUIC.

Papers already published, scheduled for publication, or intended for submission elsewhere are welcome as submissions.  The workshop will not have a formal proceedings, though we expect speakers to allow us to make their presentations available for free on the workshop website during and after the workshop.  Our intention is that this should not prejudice authors’ ability to publish their work in other, more formal venues before or after the workshop.  Authors of accepted submissions are also strongly encouraged to make their papers available to the community as preprints through the usual channels.

Submissions should be non-anonymous, and consist of a main body and well-marked appendices. For papers that have already been published or accepted for publication already, submission should include a cover letter (at most 2 pages) commenting on what the workshop presentation would contain, appended with the accepted/published paper. For papers not already formally published, the main body should be at most 12 pages in length, in single-column format, with reasonable margins and fonts. If a work is currently in submission to a different venue, please note this in your submission. Such works will not be considered “double submissions”, and are welcome at this workshop. Appendices are unlimited in length; however, Workshop Technical Programme Committee members may base their decisions solely on the contents of the main bodies of submissions.

## Submission Website

Please submit through [EasyChair](https://easychair.org/conferences/?conf=quips20)

## Important Dates

All deadlines are 11:59pm anywhere on earth (UTC-12)

- December 13, 2019: submission deadline
- January 17, 2020: author notification
- Februrary 7, 2020: camera-ready version deadline
- February 23-26, 2020: NDSS Symposium

## Program Committee

- Cas Cremers, CISPA Helmholtz Center for Information Security
- Antoine Delignat-Lavaud, Microsoft Research (co-chair)
- Felix Günther, University of California San Diego
- Christian Huitema, Private Octopus
- Subodh Iyengar, Facebook
- Adam Langley, Google
- Bryan Parno, Carnegie Mellon University
- Adrian Perrig, ETH Zurich
- Martin Thomson, Mozilla
- Christopher Wood, Apple (co-chair)

## Location

Catamaran Resort Hotel & Spa, San Diego, California, United States.

## See Also

* [TLS 1.3 -- Ready or Not](https://www.ndss-symposium.org/ndss2016/tron-workshop-programme/)

----
