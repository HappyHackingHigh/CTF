# 編碼與解碼:

編碼與解碼是資訊領域常使用的技術

Ascii、Base64、Base32各有其適用處

# encode_and_decode_1:
>*  Ascii 20
>*  ASCII(American Standard Code for Information Interchange)美國資訊交換標準代碼是基於拉丁字母的一套電腦編碼系統
>*  ASCII是現今最通用的單字元編碼系統。
>*  https://en.wikipedia.org/wiki/ASCII
>*  https://www.asciitable.com/
>*  https://www.w3schools.com/charsets/ref_html_ascii.asp

# encode_and_decode_2:
>* Base64 20
>* https://en.wikipedia.org/wiki/Base64
>* 使用線上工具解題
>* 使用python程式解題


# encode_and_decode_3:

>* Base32 20
>* https://en.wikipedia.org/wiki/Base32


# encode_and_decode_4:

>* Morse code 20
>* https://en.wikipedia.org/wiki/Morse_code
>* 使用線上工具解題
```
https://morsecode.scphillips.com/translator.html
```

# encode_and_decode_5:

>*  angstromCTF 2016 : what-the-hex 20
>* 

解題步驟1:

```
echo "6236343a20615735305a584a755a58526659323975646d567963326c76626c3930623239736331397962324e72" | xxd -r -p
```

解題步驟2:
```
echo aW50ZXJuZXRfY29udmVyc2lvbl90b29sc19yb2Nr | base64 -d
```

# encode_and_decode_6:

>*  Internetwache CTF 2016: The hidden message 50
>*  https://www.xil.se/post/internetwache-2016-misc-50-arturo182/
>*  8進位==>轉成字串(Octal to string)==>再base64

解題步驟1:
```
0000000 126 062 126 163 142 103 102 153 142 062 065 154 111 121 157 113
0000020 122 155 170 150 132 172 157 147 123 126 144 067 124 152 102 146
0000040 115 107 065 154 130 062 116 150 142 154 071 172 144 104 102 167
0000060 130 063 153 167 144 130 060 113 012
0000071
```
使用線上工具解題 ==> http://www.unit-conversion.info/texttools/octal/

使用python解題
```
import string

res = ''
f = open('README.txt')
for line in f:
    res = res + ''.join([chr(string.atoi(x, base=8)) for x in line.split(' ')[1::]])

print res
```


# encode_and_decode_7:

>*  SECCON CTF 2014: Easy Cipher 100
>*  https://github.com/S42X/CTF/blob/master/SECCON/EasyCipher.md

解題:

```
#!/usr/bin/python

c = '87 101 108 1100011 0157 6d 0145 040 116 0157 100000 0164 104 1100101 32 0123 69 67 0103 1001111 \
     1001110 040 062 060 49 064 100000 0157 110 6c 0151 1101110 101 040 0103 1010100 70 101110 0124 \
     1101000 101 100000 1010011 1000101 67 0103 4f 4e 100000 105 1110011 040 116 1101000 0145 040 \
     1100010 0151 103 103 0145 1110011 0164 100000 1101000 0141 99 6b 1100101 0162 32 0143 111 1101110\
     1110100 101 0163 0164 040 0151 0156 040 74 0141 1110000 1100001 0156 056 4f 0157 0160 115 44 040\
     0171 1101111 117 100000 1110111 0141 0156 1110100 32 0164 6f 32 6b 1101110 1101111 1110111 100000\
     0164 1101000 0145 040 0146 6c 97 1100111 2c 100000 0144 111 110 100111 116 100000 1111001 6f 117\
     63 0110 1100101 0162 0145 100000 1111001 111 117 100000 97 114 0145 46 1010011 0105 0103 67 79\
     1001110 123 87 110011 110001 67 110000 1001101 32 55 060 100000 110111 0110 110011 32 53 51 0103\
     0103 060 0116 040 5a 0117 73 0101 7d 1001000 0141 1110110 1100101 100000 102 0165 0156 33'
     
flag = ""
for _ in c.split(' '):
  if len(_) == 2 and _[1:].isalpha(): #HEX
    flag += _.decode('hex')
  if (len(_) == 2 and not _[1:].isalpha()) or (len(_) == 3 and int(_[0]) != 0): #DEC
    flag += chr(int(_))
  if len(_) == 4 or (len(_) == 3 and int(_[0]) == 0) : #OCT
    flag += chr(int(_, 8))
  if len(_) > 4: #BIN
    flag += binascii.unhexlify('%x' % int(_,2))
print flag
```
```
import sys
import binascii
import string

def loadlist(infile):
	tlist = []
	for line in open(infile,'r'):
		for w in line.split(): tlist.append(w.lower())
	return tlist

# first argument: binary/octal/decimal/hexadecimal input
if len(sys.argv) != 2: sys.exit(2)

words = loadlist(sys.argv[1])
chars = set('abcdef')
msg = ''
for w in words:
	try:
		msg+=binascii.unhexlify('%x' % int(w,2))
	except (ValueError, TypeError) as e:
		if any((c in chars) for c in w):
			msg+=w.decode('hex')
			continue
		if w[0] == '0':
			msg+=chr(string.atoi(w, base=8))
			continue
		msg+=chr(int(w))
print msg
```


# encode_and_decode_8:

>*  alexctf-2017: CR1: Ultracoded 50
>*  https://fadec0d3.blogspot.tw/2017/02/alexctf-2017-crypto.html
>*  https://0xd13a.github.io/ctfs/alexctf2017/ultracoded/

解題:
```
from pwn import *
import morse_talk as mtalk

with open('zero_one', 'r') as f:
    data = f.read().translate(None, ' \n')

data = data.replace("ZERO","0").replace("ONE","1")
data = b64d(''.join(chr(int(data[i:i+8], 2)) for i in xrange(0, len(data), 8)))

data = mtalk.decode(data)

print data
```


# encode_and_decode_9:
>*  DNA編碼學
>*  qiwi_infosec_ctf_2016_crypto_100 100
>*  https://github.com/USCGA/writeups/tree/master/online_ctfs/qiwi_infosec_ctf_2016/crypto_100_3_COMPLETE

解題:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# @Author: John Hammond
# @Date:   2016-11-18 12:51:23
# @Last Modified by:   John Hammond
# @Last Modified time: 2016-11-18 13:12:51

mapping = {
		
		'CGA': 'A',
		'CCA': 'B',
		'GTT': 'C',
		'TTG': 'D',
		'GGC': 'E',
		'GGT': 'F',
		'TTT': 'G',
		'CGC': 'H',
		'ATG': 'I',
		'AGT': 'J',
		'AAG': 'K',
		'TGC': 'L',
		'TCC': 'M',
		'TCT': 'N',
		'GGA': 'O',
		'GTG': 'P',
		'AAC': 'Q',
		'TCA': 'R',
		'ACG': 'S',
		'TTC': 'T',
		'CTG': 'U',
		'CCT': 'V',
		'CCG': 'W',
		'CTA': 'X',
		'AAA': 'Y',
		'CTT': 'Z',
		'ATA': ' ',
		'TCG': ',',
		'GAT': '.',
		'GCT': ':',
		'ACT': '0',
		'ACC': '1',
		'TAG': '2',
		'GCA': '3',
		'GAG': '4',
		'AGA': '5',
		'TTA': '6',
		'ACA': '7',
		'AGG': '8',
		'GCG': '9'
}

def decode_dna( string ):

	pieces = []
	for i in range( 0, len(string), 3 ):
		piece =  string[i:i+3]
		# pieces.append()
		pieces.append( mapping[piece] )

	return "".join(pieces)

string = 'GGTTCAATGGGCTTGTCAATGGTTCGCATATCCATGGGCACGGTTCGCGGCTCA'	
print decode_dna(string)
```
