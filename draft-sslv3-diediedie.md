---
title: Deprecating Secure Sockets Layer Version 3.0
abbrev: SSLv3 Considered Harmful
docname: draft-sslv3-must-die-00
date: 2014-10-20
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
  I-D.ietf-tls-ssl-version3:
  I-D.ietf-tls-prohibiting-rc4:
  RFC5246:
  RFC6101:
  RFC7366:

informative:
  RFC6176:


--- abstract

Secure Sockets Layer version 3.0 (SSLv3) [[I-D.ietf-tls-ssl-version3]] is no
longer secure.  SSLv3 should not be used.  The replacement versions, in
particular Transport Layer Security (TLS) 1.2 [[RFC5246]], are considerably more
secure and capable protocols.

--- middle

# Introduction

TODO

# A Litany of Attacks



# IANA Considerations

This document has no IANA actions.

# Security Considerations

This entire document is about security.
