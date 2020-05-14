IOTA Experience Team:  
Meeting Minute
===

###### tags: `X-Team` `Meeting` `kickoff`

:::info
- **Location:** Jitsi
- **Date:** Apr 28, 2020 6:00 PM (UTC)
- **Agenda**
1. KickOff `20min`
   > [name=Antonio]
3. IOTA Streams Introduction and goals proposal `45min`
   > [name=Vlad]
4. Q&A
- **Participants:**
    - Antonio (AN)
    - Vlad (VS)
    - Markus (herrpunkt)
    - SteveK
    - Vid201#2421
    - Huhn
    - Thibault Martinez
    - Dave [EF]
    - reiloy#1823
    - nuriel77
    - Dave [IF]
    - Charlie [IF]
    - Johnathan Shaffer [IF]
    - Jack Kerouac
    - Thoralf
    - Mat Yarger [IF]
    - rck
    - m
    - dr. Electron
    - XeeVee
    - Martin K.
    - Holger Köther [IF]
    - Daniel Thompson-Yvetot [IF]
- **Contact:** Antonio Nardella <antonio.nardella@iota.org>
- **Host:** AN
- **Reference:** - [GitHub issue](https://github.com/iota-community/iota-experience-team/issues/1)

:::

(Meeting is being recorded and will be published to a video streaming platform)


Antonio: Introduction to the IOTA Experience Team with presentation
Vlad: Introduction to IOTA Streams

:dart: IOTA Experience Team Kickoff - IOTA Streams
---
The goals have up to three priorities. A for highest, C for lowest

#### IOTA Streams Feedback (A)
- Provide feedback over the IOTA Streams
- Share your needs

#### “Channels Application step-by-step” joint blog post series (B)
The goal of the post is to explain in some detail decisions behind Channels - app messages and API. The post can consist of the following short sections:
- main goal is to provide privacy and integrity -- hence TaggedPacket;
- next, payload messages can be authenticated by Author in SignedPacket, hence Author needs signature (MSS) keypair;
- Author's public key and Channel address must be bound, hence Announcement message;
- need for Author's MSS keypair change, hence ChangeKey message;
- session keys must be exchanged somehow, hence Keyload message;
- public key based key exchange, hence Subscriber's NTRU keypair;
- subscription mechanism is enabled with Subscribe/Unsubscribe messages, Subscriber’s NTRU public key is protected, hence Author's NTRU keypair;
- messages can be linked in different ways, hence tree-like topology and links mechanism.

#### Select optimal Spongos PRP and hash function for embedded devices \(C\)
Spongos transform (PRP) and hash function directly impact performance of message processing and hash-based crypto (WOTS, MSS). Current choice of Troika and Keccak-F[1600] may not be the best choice for binary or embedded devices.
A possible plan includes the following steps:
1. Consider sponge-based algorithms
https://csrc.nist.gov/Projects/Lightweight-Cryptography
https://competitions.cr.yp.to/caesar-submissions.html
http://bench.cr.yp.to/primitives-aead.html
and hash-functions
https://blake2.net/
http://bench.cr.yp.to/primitives-hash.html
2. Run benchmarks on different platforms (PC, raspberryPi, android, etc.); compare results against Troika and Keccak-F[1600] permutations
3. Add implementations for PRP trait (https://github.com/iotaledger/streams/blob/master/iota-streams-core/src/sponge/prp/prp.rs#L12) and Hash trait (https://github.com/iotaledger/streams/blob/master/iota-streams-core/src/hash/mod.rs#L8)

#### Improve benchmarks \(C\)
Currently low-level crypto algorithms (Spongos PRP, WOTS and MSS) are benchmarked. 
1. Make benchmarks more generic to allow benchmarking Spongos encryption with any PRP
1. Add benchmarks for Channels application, consider several use-cases: with short/medium/long messages, signed/unsigned packets, with/without NTRU keys, etc.
1. Report benchmark results in wiki/docs


#### IOTA Streams Integrations (B)
1. Compile IOTA Streams rust library for wasm target
1. Add convenience wrappers at javascript level
1. Integrate Channels app instead of MAM0 into existing projects

#### Serialization for Channels app using Protobuf3 library \(C\)
Implement Channels application serialization:
Select Author's and Subscriber's state variables (own keypair, trusted public keys, spongos states, etc.) (see https://github.com/iotaledger/streams/blob/master/iota-streams-app-channels/src/api/author.rs, https://github.com/iotaledger/streams/blob/master/iota-streams-app-channels/src/api/subscriber.rs);
add new message types: AuthorState, SubscriberState (see https://github.com/iotaledger/streams/blob/master/iota-streams-app-channels/src/message/mod.rs), implement ContextWrap, ContextUnwrap traits;
add API methods to serialize states.



:busts_in_silhouette: Q&A Round
---

**Q**: How much time is necessary to participate in?
  
**A**: This completely depends on your availability. Already by engaging 1h/week you can contribute on different goals.

**Q**: How much experience is recommended/required?
  
**A**: Experience is very subjective.. I'd say that to have fresh eyes on our software also helps us see things that we give for granted and might be even more helpful to make it a better experience for people approaching IOTA for the first time, while if you want to provide a proof-of-concept, more experience in IOTA will help you develop it faster..

**Q**:What does "Create a list of RFP’s for the EDF to fund Open Source development" mean? Is it like a soft-due-diligence to pre-filter the proposals before they get to the IF EDF team?
  
**A**: Example: the Experience team is working on Streams, and then we realize "wouldn't it be nice to have a simple to use npm package for this?"
Then this input would be provided to the EDF team (Mark primarily) and we can make a Request for Proposal for that particular task
So the Experience team essentially finds gaps in what is being offered right now by our products, and how to further extend / improve them



:writing_hand: Notes
---
<!-- Other important details discussed during the meeting can be entered here. -->
