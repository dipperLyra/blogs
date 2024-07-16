# Know Your Meter (KYM)

If you love puzzles, there is a giant puzzle machine in your house, your prepaid electric meter :)

Until yesterday, I never saw this machine as a puzzle machine that it is. When things just work, you tend not to think about them. Yesterday, for the first time, the prepaid electric meter failed to just work. Typically you would purchase a token and the only struggle would be to use the clumsy old keyboard to input the token digits. I did that several times, painstakingly entering the correct digits over and over again but no unit would reflect on the dull LCD screen. It would show some sign of loading and afterwards display zero (0).

I reached out to some friends, they said I should read up on KCT (Key Change Token). The energy company of Abuja has a [page](https://www.abujaelectricity.com/about-tid-rollover/) on how to do this but I could not find any indepth technical details on their page on what exactly is happening. They mentioned something about TID rollover: TID Rollover is the process of updating such meters to enable them continue to function seamlessly.

## Why should we be updating the TID and what is the TID?

According to [tidrollover.com] (https://tidrollover.com/What-is-TID/Introduction-to-TID), The Token Identifier (TID) is a 24-bit field, contained in STS compliant tokens, that identifies the date and time of the token generation.

This means that TID is a 24 bits field for representing minutes that has elapsed since 1993 when the [STS standard](https://www.sts.org.za/#gsc.tab=0) was widely adopted. The meter uses an internal 24 bits counter to keep state of the TID. Therefore when the counter reaches its MOD (maximum number) there will be need for a reset. The TID rollover means reseting the meter's internal states, like base year which was 1993, counter to initial state, etc. The KCTs are encoded instructions that are used for this update.

### Why are the TIDs expiring now?

The TIDs with base years 1993 are expiring because they have reached 31 years which is the maximum number of years they can count in minutes.

What is the bad luck with 31, how do we know that it is the maximum year this counter can count? There is nothing special about 31, only that it is the maximum number in minutes that can be held by the 24 bits counter.

### Counter modulus (max count) can be calculated like this:

2 raised to the power of the number of bits, 2^24 = 16,777,216 ∴ the counter can count upto 16,777,216 minutes.

Convert 16,777,216 minutes to years:

number of minutes in 1 year, 365 * 24 * 60 = 525 600 minutes/year
number of years in 16,777,216 minutes => 16777216 / 525600 = 31.9 years.

Taking a floor of this number gives you => floor (31.9) = 31 years.

In summary we are updating our meters because the counter inside has reached its maximum number. Of course, the energy companies might take advantage of this process to update other details stored in the meter firmware.

If you are interested in the puzzle part mentioned in the beginning, consider breaking the encryption keys used by the meter. The meters do not talk to any server, at least the Keypad meters, they use an internal key and protocol to decrypt the token digits. The prepaid recharge token is an encoded piece of information that contains details like:

- Meter Identifier
- Token Type
- Token Expiry Date
- Credit Amount
- Checksum
- Encryption Key

Enjoy cracking the puzzle :)
