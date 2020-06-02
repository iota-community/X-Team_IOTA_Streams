IOTA Experience Team:  
Meeting Minute
===

###### tags: `X-Team` `Meeting` `kickoff`

:::info
- **Location:** Jitsi
- **Date:** Jun 02, 2020 6:00 PM (UTC)
- **Agenda**
1. Welcome `10min`
   > [name=Antonio]
3. IOTA Streams `20min`
   > [name=Vlad]
4. Q&A
- **Participants:**
    - Antonio (AN)
    - Vlad (VS)
    - rck
    - Thoralf
    - herrkpunkt
    - AleB
    - reiloy#1823
    - Dr.Electron
    - huhn
    - Critical
    
- **Contact:** Antonio Nardella <antonio.nardella@iota.org>
- **Host:** AN
- **Reference:** - [GitHub PR]()

:::

(Meeting is being recorded and will be published to a video streaming platform)


:dart: IOTA Experience Team - IOTA Streams
---

Discuss IOTA Streams development and community goals.

AN: Brief introduction and thank you to AleB and riley (gallegogt)

VS:
* Presentation - Message types in IOTA Streams
* Links - Cryptographically linked messages to reduce key exchange overhead and reduce secret managing overhead
* Main transport for IOTA Streams we are focusing on is the Tangle.
* Navigation in message tree

* Publishing a message
* Querying the Tangle
* Spamming attack
* What is the source of the issues?
* Solutions!

:busts_in_silhouette: Q&A Round
---
For a simple anti spam measure, we could distribute the bundle hash along with the tag, right?
...

Is the streams lib restructured with chrysalis or coordicide? or is this just a change of the base iota lib and streams can normally work without further work?
...

When sending a Author Signed Message how to know if all keys of MSS are used?
...

Any update on state serialization (#14), so that from a seed one can recover the state of author and subscriber ?
...


Can we get an example how to use another transport medium for IOTA Streams? Some small example code for that would be nice. I think this will be an important feature for embedded devices
...


Regarding serialization, I think the seed should be part of the serialized state. This has worked nicely in v1. Of course there has to be a way to encrypt the state object.
...


Are there plans for another Language support in the near future? I would really like to test the performance on MCUs or other low ressource devices.
...


:writing_hand: Notes
---
<!-- Other important details discussed during the meeting can be entered here. -->
