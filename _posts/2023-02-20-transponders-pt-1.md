---
title: "Transponders, part 1"
date: 2023-02-20
---

I thought I'd give this blogging thing a go while I'm waiting for some equipment to arrive. Here goes nothing.

# Intro blab

I've been trying to learn about this thing called [transponders](https://en.wikipedia.org/wiki/Transponder) and how to make use of them. They're used in a bunch of places where there's a need to track something, like a bar code but you can actually talk to it in an electromagnetic kind of way and get an answer back. They came about way before cheap cameras and processing power to support it, and they're still in use today. You can read more on that Wikipedia page if you want to. This part will just be some general blabbing on the topic to get you a bit up to speed, and we'll get into the details in the next ones maybe. And no, I won't be telling you how to bypass any of it.

One very specific use of this tech is in automobile immobilizers. See, at some point people learned the most luxurious cars could be hotwired and taken for a joyride. As it turned out, not everyone was happy about that, including car owners and insurance companies. So them big automotive companies had to think of a way to make stealing a car harder for your average teenager, and the answer they came back with was The Immobilizer.

The idea behind the system was, since we already have a computer in the car anyway (the [Engine Control Unit](https://en.wikipedia.org/wiki/Engine_control_unit), or ECU for short), why not task it with identity verification as well, and allow engine start only when the user presents a valid token. Some designs have immobilizers integrated into the ECU, others have a separate immbilizer box connected to the ECU instead. In the designs I'm aware of, the token takes the form of a small transponder built into the key, the same key used for starting the car, so it can be interrogated whenever you try to start the car. So not only you have to have the right key, the transponder chip has to satisfy the immobilizer box too; this makes hotwiring -- in theory -- ineffective.

![A bunch of transponder devices so you know what they look like. Taken from a random place on the internet.](/blarg/assets/20230220/transponders.jpg)

Whether the same transponder device is responsible for unlocking the doors and disabling the alarm is implementation dependent; for all I care, these are two totally separate devices. If anything, many transponder designs come in completely sealed packages with no electrical connections sticking out or anything like that.

# Theory of operation of a fixed-code system, or something

So how do this stuff works? Well, this is what the whole series of post-its will be about.

On the very high level, the whole system is comprised of three little boxes:

* The transponder, the "something you have" thing
* The reader, the "I know how to talk to this" thing
* The immobilizer box, the "I am the bouncer here" thing

The immobilizer uses the reader to talk to the transponder when it feels like it wants to make sure the right key is in the lock, and it does so using electromagnetism. Remember, the transponder is completely isolated? So to do anything at all, on command, the reader transmits some amount of power to the transponder by creating an electromagnetic field around it. The transponder charges up, spits out its identification code by using the magic of electromagnetism, and goes back to sleep. The reader then interprets the aether vibrations and spits out the ID data in the form that normal electronics can understand -- bits, bytes, etc.

![Overall scheme of things, depicting how the reader interacts with the transponder. Taken from TI SCBU020.](/blarg/assets/20230220/overall-scheme-of-things.png)

And that's kinda it. That's how fixed-code immobilizer systems work; nothing magical except for electromagnetism. As it turned out, the teenagers were smart enough to figure out you can sniff this magical fixed code, replay it as needed, and oh wow we got us a joyride again.

# Round 2: the challenged

I imagine that someone smart in the room has pointed out that transmitting the secret over the air in plaintext might not have been such a brilliant idea after all. How about we use the secret to implement a challenge-response authentication protocol (no acronym this time, strangely enough) so as to make replay attacks impossible.

In this scheme, the immobilizer would generate a challenge -- some number, which, crucially, should only be used once -- and pass it to the transponder using the reader doodad. The transponder then take this challenge number and the very secret key inside of it, mash it together in some way, and return the response back to the immobilizer. The immobilizer does the same and compares the results; if they match, then it gives the ECU a-ok to get going. No secrets transmitted, no joyrides for them youngsters either. You'd think they could have done this right from the start, no?..

And this kinda is where we are today, I think. Algorithms get broken and improved and yes, it's based on AES now, but the general flow of things seems to be the same CRAP (challenge-response authentication protocol) like it was years ago.

# So what

Well, I said I wanted to understand how these things **really** work, didn't I. You see, someone has to provision the keys. Suppose there is the "all keys lost" situation (mhm, right) -- how do you make new keys? How do you let the immo box intimate with the new and shiny transponder, and vice versa? What exactly happens during that process? All this is part of another project, which is not that important right now.

So many questions, zero answers on the internet.

Everybody seems to be in the business of selling you magical devices that make Everything Alright for a meager sum of several hundred (or a thousand) monies, whichever currency you use. And of course, nobody knows how these doodads work -- and if they do, they keep quiet about it. Let's see if I can find anything out (yes I could, but bear with me, I have to put a hook in, don't I).

Stay tuned for part two. Love, peace, and sausages!
