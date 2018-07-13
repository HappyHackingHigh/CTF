
破密分析

# Crypto

替換式密碼Substitution cipher

[換位加密法Transposition cipher](https://en.wikipedia.org/wiki/Transposition_cipher)

[Scytale cipher密碼棒](https://en.wikipedia.org/wiki/Scytale)


# Crypto_001_最愛凱薩

>*  ABCTF 2016 : ceasar-salad-10 10

解法1:使用線上工具解題

輸入看看http://www.xarg.org/tools/caesar-cipher/

解法2:使用線上工具解題
```
暴力破解法[窮舉法] Brute Force
把所有可能的方法都執行看看
```
https://planetcalc.com/1434/

解法3:直覺法

xyzqc{t3_qelrdeq_t3_k33a3a_lk3_lc_qe3p3}==>abctf{FLAG}

解法4:使用python程式解題(作業參看其他解題)

# Crypto_002_暴力破解法的奧義
angstromCTF 2017:The Beginning

# 其他練習

>* EasyCTF 2015: Julius Save Me (20)

https://github.com/ctfs/write-ups-2015/tree/master/easyctf-2015/cryptography/julius-save-me

>* UFO CTF School 2016 : rotate-it-25
https://github.com/ctfs/write-ups-2016/tree/master/ufo-ctf-school-2016/crypto/rotate-it-25

>* EasyCTF-2014:A Simple Cipher 20
>* https://www.xarg.org/tools/caesar-cipher/

# Crypto_003_頻率分析法

>*  Pico CTF 2014 : Substitution 50
>* [替換式密碼Substitution cipherの頻率分析法](https://zh.wikipedia.org/wiki/%E9%A2%91%E7%8E%87%E5%88%86%E6%9E%90)
>* 解題:使用線上工具http://quipqiup.com/

# Crypto_004_頻率分析法續集

>*  angstromCTF 2016 : artifact-20 20
>*  https://github.com/ctfs/write-ups-2016/tree/master/angstromctf-2016/crypto/artifact-20
>*  使用線上工具http://quipqiup.com/

# Crypto_005_頻率分析法第三集
>*  angstromCTF 2017: Substitution Cipher 60
>*  

# Crypto_006_密碼棒加密法
>*  EKOPARTY CTF 2015: SCYTCRYPTO 50

解法一:

解題步驟1:

題目告訴你SCYTCrypto+又是密碼問題===>要想得到scytale-cipher

解題步驟2:善用Google看看

www.dcode.fr/scytale-cipher

解題步驟3:使用線上工具
http://www.dcode.fr/scytale-cipher


解法二:使用linux 指令fold

```
Usage: fold [OPTION]... [FILE]...
Wrap input lines in each FILE, writing to standard output.

With no FILE, or when FILE is -, read standard input.

Mandatory arguments to long options are mandatory for short options too.
  -b, --bytes         count bytes rather than columns
  -s, --spaces        break at spaces
  -w, --width=WIDTH   use WIDTH columns instead of 80
  --help     display this help and exit
  --version  output version information and exit

```
#### Crypto_007_Bacon cipher

暫未出題

angstromCTF 2016 : shakespeare-60

```
intext = "tOBeoRNottOBeTHATiStHeQueSTIONWHetHErTISnOBlERINTHeMInDtOSuffERThESlINGSaNDaRRowSOFoUTRAGEoUSFoRtuNeORTOTAkeARMSaGAINStaSEAofTRoUBlESANDbYOPpOSInGEnDTHEM"
outtext = ""
for c in intext:
    if c.isupper():
            outtext += "B"
    else:
            outtext += "A"

print outtext
'ABBAABBAAABBABBBBABABABAABBBBBBBAABBABBBABBABBBBBBABBABABBAAABBBABBABBBBABBABBAABBBABBBBBBABBBABAABABBBBBBAABBBBABBBBBAABBBAABBABBABBBBBABBBABBBABBABBBBB'
```


# Crypto_101_凱薩密碼擴充版

>* RC3 CTF 2016 : salad-100
>* https://github.com/ctfs/write-ups-2016/tree/master/rc3-ctf-2016/crypto/salad-100
>* https://github.com/ctfs/write-ups-2016/tree/master/rc3-ctf-2016/crypto/salad-100
>* 使用python程式解題
```
import string

caesaralpha = "abcdefghijklmnopqrstuvwxyz0123456789"

def caesar(input_string, rot):
    output_string = ""
    for i in range(len(input_string)):
        if input_string[i].isalnum():
            idx = (caesaralpha.find(input_string[i]) + rot) % len(caesaralpha)
            output_string += caesaralpha[idx]
        else:
            output_string += input_string[i]
    return output_string

enc = '7sj-ighm-742q3w4t' # encrypt data

for i in range(len(caesaralpha)):
    print caesar(enc, i)
```

# Transposition cipher

https://en.wikipedia.org/wiki/Transposition_cipher




# Crypto_102_Transposition cipher

>*  AlexCTF2017: Fore1-Hit_the_core 50
>*  https://isitdtu.blogspot.tw/2017/02/alexctf-2017-fore1-hit-core-forensics-50.html

解題步驟1:
```
file fore1.core 
```
解題步驟2:

$ strings fore1.core
```
….
cvqAeqacLtqazEigwiXobxrCrtuiTzahfFreqc{bnjrKwgk83kgd43j85ePgb_e_rwqr7fvbmHjklo3tews_hmkogooyf0vbnk0ii87Drfgh_n kiwutfb0ghk9ro987k5tfb_hjiouo087ptfcv}
….
```

解題步驟3:使用python解題

sol

```
cipher='cvqAeqacLtqazEigwiXobxrCrtuiTzahfFreqc{bnjrKwgk83kgd43j85ePgb_e_rwqr7fvbmHjklo3tews_hmkogooyf0vbnk0ii87Drfgh_n kiwutfb0ghk9ro987k5tfb_hjiouo087ptfcv}'

cipher=cipher[3:]
flag = ''
for x in range(0,len(cipher),1):
    if x%5==0:
        flag+=cipher[x]
print flag

```

```
cipher='cvqAeqacLtqazEigwiXobxrCrtuiTzahfFreqc{bnjrKwgk83kgd43j85ePgb_e_rwqr7fvbmHjklo3tews_hmkogooyf0vbnk0ii87Drfgh_n kiwutfb0ghk9ro987k5tfb_hjiouo087ptfcv}'

''.join(cipher[3 : : 5])
```

```
s = 'cvqAeqacLtqazEigwiXobxrCrtuiTzahfFreqc{bnjrKwgk83kgd43j85ePgb_e_rwqr7fvbmHjklo3tews_hmkogooyf0vbnk0ii87Drfgh_n kiwutfb0ghk9ro987k5tfb_hjiouo087ptfcv}'
print s[3::5]
```

python sol.py


# Crypto_103_affine-cipher

>*  School CTF 2015: affine-cipher-100(教) 150
>*  https://github.com/BurningMarshmallow/CTF/blob/master/affine_solve.py

解題:使用python程式解題

```
import string

s = string.ascii_lowercase # a-z
s += '_'
d = {}
for c in range(len(s)):
	d[s[(c*4 + 15)%27]] = s[c]
ciphertext = 'ifpmluglesecdlqp_rclfrseljpkq'
s1 = ''
for x in cr:
	s1 += d[x]
print s1
```

