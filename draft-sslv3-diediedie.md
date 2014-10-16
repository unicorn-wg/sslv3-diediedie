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
  RFC2119:
  RFC2246:
  RFC4346:
  RFC4492:
  RFC5246:
  RFC6101:
  RFC7366:

informative:
  RFC1321:
  RFC3174:
  RFC6176:
  RFC6347:
  FIPS180-2:
    title: NIST FIPS 180-2, Secure Hash Standard
    author:
      name: NIST
      ins: National Institute of Standards and Technology, U.S. Department of Commerce
    date: 2002-08
  POODLE:
    target: http://googleonlinesecurity.blogspot.com/2014/10/this-poodle-bites-exploiting-ssl-30.html
    title: This POODLE bites.. exploiting the SSL 3.0 fallback
    author:
      name: Bodo Moeller
      ins: B. Moeller
    date: 2014-10-14



--- abstract



Secure Sockets Layer version 3.0 (SSLv3) [SSLv3] is no longer secure.  This
document requires that SSLv3 not be used.  The replacement versions, in
particular Transport Layer Security (TLS) 1.2 [RFC5246], are considerably more
secure and capable protocols.

This document updates the backward compatibility sections of the TLS RFCs to
prohibit fallback to SSLv3.

--- middle

# Introduction

The SSLv3 handshake has been subject to a long series of attacks, as well as
gradual weakening of the cipher suites it supports since it was released in
1996.  Despite being replaced by TLS 1.0 [RFC2246] in 1999, and subsequently TLS
1.1 in 2002 [RFC4346] and 1.2 in 2006 [RFC5246], availability of these
replacement versions has not been universal.  As a result, many implementations
of TLS have permitted the negotiation of SSLv3.

The predecessor of SSLv3, SSL version 2, is no longer considered secure
[RFC6176].  SSLv3 now follows.

SSLv3 MUST NOT be used [RFC2119].  Negotiation of SSLv3 from any version of TLS
MUST NOT be permitted.

# A Litany of Attacks

The cipher block chaining (CBC) modes of SSLv3 use a flawed MAC-then-encrypt
construction that has subsequently been replaced in TLS versions [RFC7366].
Unfortunately, the mechanism to correct this flaw relies on extensions: a
feature added in TLS 1.0.  SSLv3 cannot be updated to correct this flaw.

The non-deterministic padding using the CBC construction in SSLv3 further
trivially permits the recovery of plaintext [POODLE].

The flaws in the CBC modes in SSLv3 are mirrored by the weakness of the stream
ciphers it defines.  Of those defined in [SSLv3], only RC4 is currently in
widespread use.  RC4, however, exhibits serious biases and is also no longer fit
for use [I-D.ietf-tls-prohibiting-rc4].

SSLv3 also relies on SHA-1 [RFC3174] and MD5 [RFC1321] for integrity and its
fundamental pseudorandom function.  These hash algorithms are considered weak
and are being systematically replaced with stronger hash functions, such as
SHA-256 [FIPS180-2].

# Limited Capabilities

SSLv3 is unable to take advantage of the many features that have been added to
recent TLS versions.  This includes the features that are enabled by ClientHello
extensions, which SSLv3 does not support.

SSLv3 also cannot benefit from new cryptographic modes.  Of these, two are
prominent:

* Authenticated Encryption with Additional Data (AEAD) modes are added in
  [RFC5246].

* Elliptic Curve Diffie-Hellman (ECDH) and Digital Signature Algorithm (ECDSA)
  were added in [RFC4492].

Though there are many other features that are not supported, including a
datagram mode of operation [RFC6347].

# IANA Considerations

This document has no IANA actions.

# Security Considerations

This entire document aims to improve security by identifying a protocol that is
not secure.