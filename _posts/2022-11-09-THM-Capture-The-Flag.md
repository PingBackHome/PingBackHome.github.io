---
layout: post
title: TryHackMe | C4ptur3-th3-fl4g
---

# TryHackMe | C4ptur3-th3-fl4g


  
## TryHackMe Questions

**Task 1**

'c4n y0u c4p7u23 7h3 f149?'
> Can you capture the flag

'01101100 01100101 01110100 01110011 00100000 01110100 01110010 01111001 00100000 01110011 
01101111 01101101 01100101 00100000 01100010 01101001 01101110 01100001 01110010 01111001 00100000 01101111 01110101 01110100 00100001'\
SOLUTION: Binary
> lets try some binary out!

'MJQXGZJTGIQGS4ZAON2XAZLSEBRW63LNN5XCA2LOEBBVIRRHOM======'\
SOLUTION: Base 32
> base32 is super common in CTF's

'RWFjaCBCYXNlNjQgZGlnaXQgcmVwcmVzZW50cyBleGFjdGx5IDYgYml0cyBvZiBkYXRhLg=='\
SOLUTION: Base64
> Each Base64 digit represents exactly 6 bits of data.

'68 65 78 61 64 65 63 69 6d 61 6c 20 6f 72 20 62 61 73 65 31 36 3f'\
SOLUTION: Hex
> hexadecimal or base16?

'Ebgngr zr 13 cynprf!'\
SOLUTION: ROT13
> Rotate me 13 places!

'*@F DA:? >6 C:89E C@F?5 323J C:89E C@F?5 Wcf E:>6DX'\
SOLUTION: ROT47
> You spin me right round baby right round (47 times)

'- . .-.. . -.-. --- -- -- ..- -. .. -.-. .- - .. --- -.
. -. -.-. --- -.. .. -. --.'\
SOLUTION: Morse code
>TELECOMMUNICATION  ENCODING  

'85 110 112 97 99 107 32 116 104 105 115 32 66 67 68'\
SOLUTION: Decimal
> Unpack this BCD

'LS0tLS0gLi0tLS0gLi0tLS0gLS0tLS0gLS0tLS0gLi0tLS.......='\
SOLUTION: Base64 -> Morse -> Binary -> ROT47 -> Decimal
> Let's make this a bit trickier...

**Task 2**

https://academo.org/demos/spectrum-analyzer/
> Super Secret Message

**Task 3**

https://futureboy.us/stegano/decinput.html
> SpaghettiSteg

**Task 4**

'Download and get 'inside' the file. What is the first filename & extension?'
> hackerchat.png

'Get inside the archive and inspect the file carefully. Find the hidden text.'
> AHH_YOU_FOUND_ME!
