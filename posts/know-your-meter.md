---
mathjax: true
title: Know Your Meter (KYM)
---

# Know Your Meter (KYM)

If you love puzzles, there is a giant puzzle machine in your house, your prepaid electric meter :)

$a^2 + b^2 = c^2$

Until yesterday, I never saw this machine as a puzzle machine that it is. When things just work, you tend not to think about them. Yesterday, for the first time, the prepaid electric meter failed to just work. Typically you would purchase a token and the only struggle would be to use the clumsy old keyboard to input the token digits. I did that several times, painstakingly entering the correct digits over and over again but no unit would reflect on the dull LCD screen. It would show some sign of loading and afterwards display zero (0).

I reached out to some friends, they said I should read up on KCT (Key Change Token). The energy company of Abuja has a [webpage](https://www.abujaelectricity.com/about-tid-rollover/) on what to do but I could not find the technical details I wanted. They mentioned something about TID rollover: _TID Rollover is the process of updating such meters to enable them continue to function seamlessly_.

## Why should we be updating the TID and what is the TID?

According to [tidrollover.com](https://tidrollover.com/What-is-TID/Introduction-to-TID), The Token Identifier (TID) is a 24-bit field, contained in STS compliant tokens, that identifies the date and time of the token generation.

This means that TID is a 24 bits field for representing minutes that has elapsed since 1993 when the [STS Standard](https://www.sts.org.za/#gsc.tab=0) was widely adopted. The meter uses an internal 24 bits counter to keep state of the TID. Therefore when the counter reaches its MOD (maximum number) there will be need for a reset. 

The TID rollover means reseting the meter's internal states, like base year which was 1993, counter to initial state, etc. The KCTs are encoded instructions that are used for this update.

### Why are the TIDs expiring now?

The TIDs with base years 1993 are expiring because they have reached 31 years which is the maximum number of years they can count in minutes.

Why is the maximum 31years and how do we know that? There is nothing special about 31, only that it is the maximum number in minutes that can be counted by a 24 bits counter.

### Calculating TID Maximum Years

The TID uses a 24-bit counter, therefore, computing the max number of minutes that can be counted by the 24-bit counter and converting that to years will give us the answer.

Maximum count of this counter is: \( 2^{24} = 16,777,216 \) ∴ it can count up to 16,777,216 minutes.

Maximum count of this counter is: \( 2^{24} = 16,777,216 \) ∴ it can count upto 16,777,216 minutes.

#### Converting 16,777,216 minutes to years

Minutes in 1 year: \( 365 \times 24 \times 60 = 525,600 \text{ minutes/year} \)

Years in 16,777,216 minutes: <span> \( \Rightarrow \frac{16,777,216}{525,600} = 31.9 \text{ years.} \) </span>

Taking floor, <span>\( \Rightarrow \lfloor 31.9 \rfloor = 31 \)</span> years


### Summmary

In summary we are updating our meters because the counter inside has reached its maximum number. Of course, the energy companies might take advantage of this process to update other details stored in the meter firmware.

If you are interested in the puzzle part mentioned in the beginning, consider breaking the encryption keys used by the meter. The meters do not talk to any server, at least the Keypad meters, they use an internal key and protocol to decrypt the token digits. The prepaid recharge token is an encoded piece of information that contains details like:

- Meter Identifier
- Token Type
- Token Expiry Date
- Credit Amount
- Checksum
- Encryption Key

Enjoy cracking the puzzle :)
