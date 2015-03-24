BEST PRACTICES

It is strongly encouraged that any tunnel-based system exchanging private information utilizes strong cryptography at the application layer, and not rely on security that may or may not be provided at the radio layer. Even for public broadcast content, cryptographic signatures should be used to defend against impersonation and to build authenticated relationships and reputation for future communications. OTR and Axiotl both provide viable solutions for this, offering both perfect forward secrecy and public key verification. Axiotl's pre-keying method allows for secure sessions to be generated even if the receiving party is not available, creating a means for end-to-end encryption through multi-hop message routing.

