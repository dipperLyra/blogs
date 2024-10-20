---
title: Use App-Based Authenticator and Avoid SMS Authenticator When Available
---

# Use App-Based Authenticator, Avoid SMS OTP When Available

The technology used for common network communication (calls and text messages) not being end-to-end encrypted means that the Network Operator can record calls and other activities. That can be worrisome but there are scarier things happening deep within the cellular network stack that can drive one crazy.

I have an anecdote that has led me to start digging into phone network architectures. My mum tried calling me recently but an unknown lady picked the call. Since my mum couldn't reconcile the voice calling her "mummy" with mine, she cut the call. Later, on the same day, I tried calling my mum and a guy that sounded like a drunk picked the phone, we had a brief conversation. I asked him where the owner of the phone was and other very short questions, he parried all. Freaked out, I called my sis immediately who retried my mum's number and got through, that is, my mum picked the phone.

What happened at first? I don't know, I was terribly confused. I suspected MTN (the network Operator) might be glitching. I spoke with a friend in Cybersecurity and he pointed me to this [video](https://www.youtube.com/watch?v=wVyu7NB7W6Y) which he had sent to me earlier the same week but I never watched it :) The video gave me the clues I needed. It is very likely that I have been made a third wheeler by an attacker in the middle.

![Third-wheeler](../resources/third-wheeler.jpeg)

Summary of the video is that phone networks are not very secure. In fact, it is relatively easy to fake that you are a telco and get information from another telco about their users.  If you purchase an [SS7](https://en.wikipedia.org/wiki/Signalling_System_No._7) (Signaling System No. 7) license or know a shady SS7 license owner you can do a lot. One being, taking or hijacking calls and text messages meant for another person without the person ever knowing. Cell tower triangulation is pretty accurate for tracking people. Many security companies own this license and we assume that they are all good actors :) Something tells me that if you look closely there would be willing dealers on Telegram and Darkweb selling access to this protocol.

I am still grappling with a lot of new information but for now I would keep to these and advise others to do the same:

- Check all email account settings, use app-based authentication or (device) push notification for 2FA. Email is the one ring that rules our digital security. If it is cracked, almost nothings else can hold.
- Always use app-based authentication for 2FA where possible. Avoid SMS 2FA whenever possible.
- Use a physical token device for bank apps. Most Nigerian banks offer physical token for 2FA and not app-based which is more common among FinTechs and neobanks.
- Important phone calls or text messages should all be on end-to-end encrypted platforms. E.g. WhatsApp, Signal, etc.

## Key words for further reading

2FA: Two Factor Authentication
App-based authenticators: Google Authenticator, Duo Mobile, etc.
SS7: Signaling System No. 7
What is SS7 Attack and how does it work: [link](https://www.reddit.com/r/AskNetsec/comments/s0t5za/what_is_an_ss7_attack_and_how_does_it_work/)
Cellular Network: [Telecom network](https://en.wikipedia.org/wiki/Cellular_network)
