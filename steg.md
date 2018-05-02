# Steg-1

STEG(必) 20

# Steg-2
sCTF 2016 Q1 : banana-boy-20(必) 50

# Steg-2
BITSCTF 2017 : black-hole-10 20

# Steg-2
CSAW Quals CTF 2013: Black & White 50

# Steg-2
BITSCTF 2017 : flagception-30
50

# Steg-2
CSAW QUALS 2015: keep-calm-and-ctf(必)
50

# Steg-2
ABCTF 2016 : just-open-it(必)
50

# Steg-2
ABCTF 2016 : gz-30
60

# Steg-2
ABCTF 2016 : best-ganondorf-50
60

http://blog.squareroots.de/en/2014/08/hitcon-ctf-2014-puzzle/

解題步驟1:查看檔案格式
```
root@kali:~/Desktop# file ezmonay.jpg
ezmonay.jpg: PDP-11 UNIX/RT ldp
```

解題步驟2:上網看看檔案特徵
[List of file signatures檔案格式特徵](https://en.wikipedia.org/wiki/List_of_file_signatures)

找出jpg的檔案特徵

解題步驟3:使用xxd查看題目的檔案格式
```
root@kali:~/Desktop# xxd ezmonay.jpg | head 
```


解題步驟4:修改成正確的檔案格式
```
root@kali:~/Desktop# printf '\xff\xd8\xff' | dd of=ezmonay.jpg bs=1 seek=0 conv=notrunc
```
解題步驟5:確認是否已經修改正確
```
root@kali:~/Desktop# file ezmonay.jpg
ezmonay.jpg: JPEG image data
```

```
root@kali:~/Desktop# xxd ezmonay.jpg | head 
00000000: ffd8 ff00 4800 4800 00ff db00 4300 0302  ....H.H.....C...
```


解題步驟6:打開修正後的圖片幾可得到解答

###### xxd

xxd:將一個檔案以十六進位的形式顯示出來
```
xxd -h

Usage:
       xxd [options] [infile [outfile]]
    or
       xxd -r [-s [-]offset] [-c cols] [-ps] [infile [outfile]]
```
```
Options:
    -a          toggle autoskip: A single '*' replaces nul-lines. Default off.
    -b          binary digit dump (incompatible with -ps,-i,-r). Default hex.
    -c cols     format <cols> octets per line. Default 16 (-i: 12, -ps: 30).
    -E          show characters in EBCDIC. Default ASCII.
    -e          little-endian dump (incompatible with -ps,-i,-r).
    -g          number of octets per group in normal output. Default 2 (-e: 4).
    -h          print this summary.
    -i          output in C include file style.
    -l len      stop after <len> octets.
    -o off      add <off> to the displayed file position.
    -ps         output in postscript plain hexdump style.
    -r          reverse operation: convert (or patch) hexdump into binary.
    -r -s off   revert with <off> added to file positions found in hexdump.
    -s [+][-]seek  start at <seek> bytes abs. (or +: rel.) infile offset.
    -u          use upper case hex letters.
    -v          show version: "xxd V1.10 27oct98 by Juergen Weigert".
```
