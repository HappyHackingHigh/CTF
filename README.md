# CTF

AngstromCTF 2018

https://medium.com/bugbountywriteup/angstromctf-writeups-4e3d51c3dc42

https://rawsec.ml/en/angstromCTF-2018-write-ups/

google-ctf-2016/forensics/

https://github.com/ctfs/write-ups-2016/tree/master/google-ctf-2016/forensics


https://writeups.amosng.com/

Forensics

HSCTF_2017: Basic Bucketfill


https://github.com/LFlare/ctf-writeups


# Linux-CTF

EasyCTF_2018: Haystack

EasyCTF_2018: Diff

https://writeups.amosng.com/2018/easyctf_2018/forensics/diff_100/

EasyCTF_2018: Remember Me==> Audio Steg

https://writeups.amosng.com/2018/easyctf_2018/forensics/remember-me_130/


### EasyCTF_2018: Special Endings

https://writeups.amosng.com/2018/easyctf_2018/forensics/special-endings_350/

### DEFCON oCTF 2016 - ultra_encryption

https://github.com/ctfs/write-ups-2016/tree/master/open-ctf-2016/steganography

>* https://github.com/ctfs/write-ups-2016/blob/master/open-ctf-2016/steganography/ultra-encryption-100/delimitry_solve.py

>* https://gist.github.com/Grazfather/cd4f8d61a2fefebea22cf5243fe97386

```
# This was done after the ctf

cts = [
    "BUEF9r9AOjw6w8XSgaZJeD==",
    "B9cb4emh7PKbfdg/OmKwl1==",
    "CjbfcYrqVbnZt04GGy5Esn==",
    "EMmqj/C0uWU8u2CMsvVtwl==",
    "EkkUe6ukmUA90AvCXnJSTG==",
    "Exjf76M+iY5s54GPGewKzj==",
    "KLBgknyMMvzHtcHPMQeEl2==",
    "KObXGzaPyeBslLDa2Zq5ub==",
    "LBwcZGGubGgYQ0s1htxQBl==",
    "LFnBkAcTJggtxL05OnHz5v==",
    "NKqFajWjVHYxETwQnQbtDG==",
    "NSwcEVoClwiOMxSrPvRrTd==",
    "NoIO47zmSYiZqwC8fT/pU3==",
    "O2PEbFfrNAkYlvYb3SrUep==",
    "QXejobMGNaPdtucwzOOWPl==",
    "T5pJ8ETECCji9Mi3V9HqbP==",
    "WJk8kU8Zr2gWt7TxWwm+V3==",
    "WhPTHEtxhGlPyb91+3dY1j==",
    "W8Ln8JcRwqpZ7XBie+vyQ2==",
    "Xz0Uk6TOBTCM4xFQN6JjwY==",
    "YT/FXOl30uFQKJFwkohUUz==",
    "Ytpg0b6tk7m8j5jyIqf69U==",
    "cPX1dEYzw3lBelelIzShHn==",
    "dy6p1QWv1aSA7ghFffk+ZS==",
    "eSo1nPg0AtyqLSwjJwlfT2==",
    "ev4deqh2UAOGq0NmpgFYYL==",
    "gXMBfkV73eQgMWGHYU/ZAl==",
    "i+iAqBixR90EFO91rSex0/==",
    "jJ/gDFMT/aCedlqlGXgasT==",
    "jMqXjRO2K56OFQ6/b5GotR==",
    "kGDZLvY8FnuQnRggA3fgmm==",
    "l+XAj1NyFckuRe438m7/K9==",
    "mHuIOg7HriGtuYwI72BCNF==",
    "mgrnkcPH079/o2UQHa2PeP==",
    "pSBre9FcFJNU7Av59KDcdD==",
    "qaGP/t+qdwUj+eDExHTyek==",
    "sFOVGpP/7ErzUT5UB8gDSl==",
    "s/Q8/RkdxRcZjZHiu99Kx/==",
    "u07HTJV9Ml1SW1M4V6CwoH==",
    "vBgsNRKgPZjP4u457ZGdx0==",
    "vvzus9dgsbHEboF+IQWwFX==",
    "y16q5496Z4TEm1zahzyWVi==",
    "1VP9QujtD5yRD1C1L3UxOj==",
    "3EO8KdeBsFWV06PBnO8rWA==",
    "4MiCX3NLEZzg58pRf3ow9m==",
    "6X5fM08UHU2QLMr9ShisHc==",
    "6jHpCY2IrwXYc4W0kaGGh2==",
    "/3TPRDKfFC0D1xZTYPMKNs=="]

cts2 = [ct.decode("base64").encode("base64").rstrip() for ct in cts]

base64chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/"
bin_s = ""
for ct, ct2 in zip(cts, cts2):
    diff = base64chars.index(ct[-3]) - base64chars.index(ct2[-3])
    bin_s += hex(diff)[2:]

print bin_s.decode("hex")

```

