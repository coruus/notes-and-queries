# Mobile device security: Android versus iOS

Advice for non-specialists: Get an Apple product; preferably one using
their most up-to-date architecture. As soon as Apple releases a version
with a newer processor, replace it. Don't use iCloud to backup data;
triviallly vulnerable (still).

## Why iOS?

Why? Read Joanna Rutkowska's [blog][qubes_os], about designing a secure,
compartmentalized, open-source operating system. Then read Apple's [iOS
Security Guide][ios_security_guide]. The approaches are the same, and
sound. (Though Apple's implementation provides a much lower assurance
level than Qubes will when it eventually is released/works.)

Android does not, so far as I can tell, have a security design. No,
that's unfair; it *didn't* have one, so the excellent Android
security team is trying to graft something onto it.

Some comparisons on data security:

  - iOS encrypts *everything* before it hits flash memory. Android
    still encrypts only the data partition; the system partition is
    wide open. (This is changing on Android.)
  - iOS derives keys using PBKDF2 in-hardware; passwords cannot be
    brute-forced quickly -- the number of PBKDF2 iterations is set
    to take a fixed amount of time for each hardware model. Despite
    Android's recent change to scrypt-based key-derivation for
    encryption of the data partition, because the key is not
    bound to the hardware, it can, once extracted, be brute-forced
    in parallel. (See Litecoin-mining-ASICs.)

Some comparisons on the availability of remote-root exploits:

   - Android: Generally available for free for most Android phones that
     are not running an evergreen build of Android. Generally cheap for
     evergreen Android.[^android_nonstock]
   - iOS: Generally available only to intelligence agencies and those with
     extraordinarily deep pockets. (One published estimate was about a
     hundred thousand dollars; acquaintances of mine believe that
     this is rather an underestimate for click-and-pwn vulns.)

The one good thing I have to say about Android's security is that it
amuses me tremendously to watch script-kiddies exploiting my phone. I
am mostly bothered when the exploits are so trivial that I already know
about them.

For specialists: Most expensive Android phones have chips that full TZ
dual-worlds. That can be fun. Microfuses less so.


## Why update devices?

Tethered exploits for previous architectures usually become costless as
soon as a new architecture is released. (But click-to-pwn generally is
purchased under the condition it's never disclosed.)


## Why not use iCloud?

It's okay to store things that are valueless or encrypted in iCloud. You
generally don't want to use iCloud backup, however -- it unbinds your
data from the device-burned key.


[^android_nonstock]: And, frankly, since it is possible to remotely
install applications on an Android phone with access to a Google
Play browser session token, it generally isn't necessary to even have a
remote exploit; an attacker can get their own code to execute on the
system and (for phones not running stock) install idiot-vendor-written
applications that run as the system user (from which escalation to
root is trivial).

[ios_security_guide](http://images.apple.com/ipad/business/docs/iOS_Security_Feb14.pdf "iOS Security Guide - February 14, 2014")
[qubes_os](http://theinvisiblethings.blogspot.com/2013/03/introducing-qubes-odyssey-framework.html)
