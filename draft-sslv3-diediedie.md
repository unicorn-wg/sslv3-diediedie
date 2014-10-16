---
title: Deprecating Secure Sockets Layer Version 3.0
abbrev: SSLv3 Considered Harmful
docname: draft-sslv3-must-die-00
date: 2014-10
category: bcp
ipr: trust200902

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: R. Barnes
    name: Richard Barnes
    org: Mozilla
    email: rlb@ipv.sx
 -
    ins: M. Thomson
    name: Martin Thomson
    org: Mozilla
    email: martin.thomson@gmail.com


normative:
  SSLv3:
    target: https://tools.ietf.org/html/draft-ietf-tls-ssl-version3-00
    title: The SSL Protocol Version 3.0
    author:
      -
        name: Alan O. Freier
        ins: A. Freier
      -
        name: Philip Karlton
        ins: P. Karlton
      -
        name: Paul C. Kocher
        ins: P. Kocher
    date: 1996-11-18
  I-D.ietf-tls-prohibiting-rc4:
  RFC5246:
  RFC6101:
  RFC7366:

informative:
  RFC6176:


--- abstract

Secure Sockets Layer version 3.0 (SSLv3) [[SSLv3]] is no longer secure.  SSLv3
should not be used.  The replacement versions, in particular Transport Layer
Security (TLS) 1.2 [[RFC5246]], are considerably more secure and capable
protocols.

--- middle

# Introduction

TODO

# A Litany of Attacks



# IANA Considerations

This document has no IANA actions.

# Security Considerations

This entire document is about security.
