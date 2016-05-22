# Generate GPG key

**1. First, download the GPG installer for your terminal**
https://www.gnupg.org/download/

**2. Generate a GPG key-pair from your terminal**

```
$ gpg --gen-key
```

Output:
```
gpg (GnuPG/MacGPG2) 2.0.28; Copyright (C) 2015 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection?
```

**3. Choose the kind of key by typing the number, here we use RSA:**

```
1
```

Output:
```
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048)
```

**4. Choose the keysize you prefer - attention: consider that some tools might have problems with keysizes higher than 2048, e.g. yubikey**

```
2048
```

Output:
```
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
```
**5.  Now decide how long your key should be valid:**

```
2y
```

Output:
```
Key expires at Tue May 22 13:50:19 2018 CEST
Is this correct? (y/N)
```

**6. Confirm the key expiration date with yes:**

```
y
```
Output:
```
GnuPG needs to construct a user ID to identify your key.

Real name:
```
**7. Type in your real name:**

```
Johnny Crash
```

Output:
```
Email address:
```
**8. Type in your email address that is used with Github:**

```
johnny.crash@example.com
```

Output:
```
Comment:
```

**9. Type in a comment (optional but helpful to distinguish the keys upon different purposes):**

```
GPG Setup Tutorial
```

Output:
```
You selected this USER-ID:
    "Johnny Crash (GPG Setup Tutorial) <johnny.crash@example.com>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?
```

**10. Confirm or change your input:**

```
O # Okay
```

Output:
```
You need a Passphrase to protect your secret key.
```

**11. Now a separate GPG window will open and ask you to type in your passphrase twice. Attention: Save your passphrase BEFORE your confirm it in case something goes wrong.**


![passphrase.png](https://github.com/1000miles/FIL/raw/master/security/passphrase.png)

After you have verified your passphrase, your output will be:
```
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 5A7F87C2 marked as ultimately trusted
public and secret key created and signed.

gpg: checking the trustdb
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   5  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 5u
gpg: next trustdb check due at 2018-04-01
pub   2368R/5A7F87C2 2016-05-22 [expires: 2018-05-22]
      Key fingerprint = AC7D DD97 5A51 F46A A3D2  EECA CF7D A22F 5A7F 87C2
uid       [ultimate] Johnny Crash (GPG Setup Tutorial) <johnny.crash@example.com>
sub   2368R/E6490FF4 2016-05-22 [expires: 2018-05-22]
```

**12. Check all public GPG keys:**

```
$ gpg --list-keys
```
Output:
```
pub   2368R/5A7F87C2 2016-05-22 [expires: 2018-05-22]
uid       [ultimate] Johnny Crash (GPG Setup Tutorial) <johnny.crash@example.com>
sub   2368R/E6490FF4 2016-05-22 [expires: 2018-05-22]
```

**13. Check all secret GPG keys:**

```
$ gpg --list-secret-keys
```

Output:
```
sec   2368R/5A7F87C2 2016-05-22 [expires: 2018-05-22]
uid                  Johnny Crash (GPG Setup Tutorial) <johnny.crash@example.com>
ssb   2368R/E6490FF4 2016-05-22
```

**14. Let Github know about your new public GPG key:**

```
$ gpg --armor --export 5A7F87C2
```

**15. Copy your public GPG key:**

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Comment: GPGTools - https://gpgtools.org

mQE1BFdBn1MBCUDmYuFzAMBjy55kRGs5Sl6tL0LLZRs8+vg7d5vYIrjCkML53f2f
YyEgsKHTGoJkhlzrAs3psu0zuJmIkQRgjTXXGB8oQ8BB8aM4stFDdvSmC+/fPFZR
ABEWHDacvoThk2bTIiCi0d9BienN93g9fDzHz7Q5MZBwY18+pFpc7ZeNtuuL/eKm
IeUZLFGzhy57J0yRcq02Xvm4qGyRAop0mj0VAN0VpgEonum5KPuEAVbajHVsApsJ
iWm5I/9ISgJJbg5qQht6tnbDNsZt8vEv1w8hSMspJa6kSbmAAeTQ8liV839ak/Ni
ZpXBBksMEgcLez0lSDJ3mImHOBR/iLxrwQq44RaJKfZatIldhMBfy6S5rTbJxL4a
iUSK63i7NHx23EoQ3YMbdPc3tQARAQABtDxKb2hubnkgQ3Jhc2ggKEdQRyBTZXR1
cCBUdXRvcmlhbCkgPGpvaG5ueS5jcmFzaEBleGFtcGxlLmNvbT6JAWUEEwEKACcF
AldBn1MCGwMFCQPCZwAFCwkIBwMFFQoJCAsFFgIDAQACHgECF4AACgkQz32iL1p/
h8Kv7QlAtRvbePwOur8ZN44LPJ48F1CYO0AykRT7MFUlYLj2G0NaKXTvR+BSRh7w
w8phtrCb+vOnf+dAA06pptR6UEnrHbQss+zyfZmUqmqMjBRpLtlccS2EtvXw1xXe
loDrdlcO+MckGgHofQMhNLkFSmqtp3DvGpsguFUxCW33nfb+/TnQ5gK8zY37H0ra
/95rjax8VS+tkSL/1k2ONqlhe/n1ex2mdVrpaDzJwG/da0FpqBtnFqoJ8fa+d+ak
MYxKxNRGOesSxCzbTWe28Az7/GPb8ZWLb78SEB+SJhclhPaPii15PlT691+MCKsu
davnFgaiU+vF3L9QIB35HrMXzwWDYCn81yBfd/jjgkKkddVIXGcsIEsGavXbXv1R
OApPgiu/yLcBjBeM9vW5ATUEV0GfUwEJQNaUMW1DDuoart4k28OKLHYQWXg/WP7H
vvdBwyzdwKTSMwnNd4I+HmKwAaOtOILcQH2bot9xJId4oL59vCq++/ufHMavmcS+
x6UD+rSFriCY+Tlgq7QjosSg+0gCP8MmfqBdu7AQVhM/NvksGicNpCTtbKrZ5GG4
ectVQ40KsS4cfdq/meMQ2VUb33cBk2pWcFxbwF/0WmTWvO/nMsalgP+CFwIg7sUd
fY87RMItDal4yNDP7dwELAOLG1+80TreGHA6IOSeISTt3WwjhCSVaOWKTFN9Sxyp
zCg4nG6xxbSw4jLx9K7FlPIN1VbQL8ngdpezzfxZjhaAXNs0yFC/YkNgudMElZiA
fx+mzRvXAZgYyVMzxiwQEU+H7HQvnafFV7+/OuS97fEvABEBAAGJAU0EGAEKAA8F
AldBn1MCGwwFCQPCZwAACgkQz32iL1p/h8JIDAlAuK2aqx9N88VcqBUigBqxwa28
CyTh7v3V7hT7XiX6wfnIvaNe8kgvc4joPx/aAhCLS18IqNRw54QMby7+yclIQEF4
ieSHibKn8IpoJKPY+7+8AG5drBTy9O4QmPEEcnRC00WKQ2Wfasd/FvDJMHCGmonM
8a0SZViDkRe2eiW0Yt3hjgZFanWnY/xywSMFdNVCbQ/jTB3TxFpX+U5Fz8T44aG1
hp3Jvxw5ZKZQJWaM0hLhOedKzLhf06g5hV6hmOjbP6FNv8Dxo8P9rRIk84T8Blka
NioyZppo4HdU0BV5WQpIkFE5i/lYE3bXtx/IUOyUcB6178kKvyv/BMaL/+bZHk44
dof0FOPu93zh4angksTxaRY99dGwKNL5HtWMXinnhoROyUGYP5w=
=ByRU
-----END PGP PUBLIC KEY BLOCK-----
```

**16. Copy & paste the key to your Github account under:**

```
settings > SSH and GPG keys > New GPG key
```

**17. Open the `.gitconfig` file:**

```
$ vim ~/.gitconfig
```

**18. Add your secret key to the user section of your `.gitconfig` file:**

```
1 [user]
2         name = Johnny Crash
3         email = johnny.crash@example.com
4         signingkey = 5A7F87C2
```

**19. Now you are ready to sign your commits with:**

```
$ git commit -S -m "My commit message"
```
