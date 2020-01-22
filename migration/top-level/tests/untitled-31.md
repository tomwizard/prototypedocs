# HTTP Server test error "dh key too small"

If a ThousandEyes HTTP Server test \(or the HTTP Server view of a Page Load test\) fails with an SSL error and the message:

```text
routines:ssl3_check_cert_and_algorithm:dh key too small
```

​then the web server which performed TLS negotiation with the ThousandEyes Agent was configured with a Diffie-Hellman group which is cryptographically weak. Because of the insecure nature of weak Diffie-Hellman groups, many HTTP clients \(including ThousandEyes Agents\) will refuse to communicate via HTTPS with such a server.

Web servers which have been in service for many years without recent updates, or which have compatibility requirements with very old clients that cannot support newer encryption are most likely to see this error.

## Background

In 2015, a cryptographic attack called Logjam demonstrated the possibility of ​decrypting HTTPS-based communication if the attacker could capture the communications between client and server, such as capturing packets from an intermediate network device that handles the communications.  Part of the attack targets encryption schemes based on the Ephemeral Diffie-Hellman \(abbreviated as EDH or DHE\) keying algorithm, which is designed to create session keys with forward secrecy.

Web servers which use Diffie-Hellman are configured with a precomputed set of prime numbers, called a Diffie-Hellman group.  The number that is termed the "size" of the group \(the modulus size, specifically\) is proportional to the strength of the encryption key that will be created via the Diffie-Hellman calculations--the bigger the group size, the stronger the key.  Common group sizes at the time of the attack announcement were 512 bits, 768 bits and 1024 bits.

Group sizes of 512 bits and 768 bits are now [considered weak](https://weakdh.org/).  Generally, 1024 bits is the minimum accepted size but not recommended, and [2048 bits is considered best practice](https://supportforums.cisco.com/t5/security-documents/diffie-hellman-groups/ta-p/3147010). In particular OpenSSL, the library that provides HTTPS functionality for ThousandEyes and most other HTTP client software, has [deprecated 512bit and 768-bit Diffie-Hellman groups](https://www.openssl.org/blog/blog/2015/05/20/logjam-freak-upcoming-changes/). Web servers which attempt TLS negotiations using 512-bit and 768-bit Diffie-Hellman groups will cause OpenSSL-based clients to terminate the TLS negotiation. This includes the client which executes a ThousandEyes HTTP Server test.

## Error validation

To confirm that a test displaying the error message is the result of a server using a weak Diffie-Hellman group, the openssl command can be run from any system which can contact the server:

```text
openssl s_client -connect www.example.com:443 -cipher "EDH" | grep "Server Temp Key"
```

and

```text
openssl s_client -connect www.example.com:443 -cipher "DHE" | grep "Server Temp Key"
```

This output will provide the number of bits in the EDH or DHE cipher's key. The version of the openssl program must be at least 1.0.2b to produce the Server Temp Key output.

Alternatively, a packet capture of the TLS handshake between a client and the server can identify a Diffie-Hellman modulus with too few bits. For the Wireshark packet capture and display program, a display filter of:

```text
ssl.handshake.p_len < 128
```

will show SSL/TLS handshakes with a modulus \(mathematically denoted by the symbol "p"\) length of fewer than 1024 bits \(128 bytes\).

## Server remediation

Consult your web server documentation for instructions on upgrading the cryptographic libraries which perform TLS negotiation. Server software may or may not be upgradable to libraries which can be compatible with modern clients such as used by ThousandEyes tests while maintaining the weak ciphers needed for servicing old clients.

## Additional information

 As a reference, below are links to announcements regarding weak Diffie-Hellman ciphers from the makers of common browsers.

* **Google:** https://groups.google.com/a/chromium.org/forum/\#!topic/blink-dev/ShRaCsYx4lk
* **Microsoft:** https://support.microsoft.com/en-us/help/3061518/ms15-055-vulnerability-in-schannel-could-allow-information-disclosure
* **Mozilla:** https://bugzilla.mozilla.org/show\_bug.cgi?id=1138554

 Internet RFC's pertaining to commonly used Diffie-Hellman groups:

* [RFC 2409: The Internet Key Exchange \(IKE\)](https://tools.ietf.org/html/rfc2409)
* [RFC 3526: More Modular Exponential \(MODP\) Diffie-Hellman groups for Internet Key Exchange \(IKE\)](https://tools.ietf.org/html/rfc3526)
* [RFC 5114: Additional Diffie-Hellman Groups for Use with IETF Standards](https://tools.ietf.org/html/rfc5114)

