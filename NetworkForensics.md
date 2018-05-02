
# TSCTF 2017 : woodstock-1-10

>* https://github.com/USCGA/writeups/tree/master/online_ctfs/bitsctf_2017/woodstock

```
strings ws1_2.pcapng |grep -oE "BITSCTF{.*}" --color=never
```

# CSAW Quals CTF 2013: Networking 1

>* https://github.com/ctfs/write-ups-2013/tree/master/csaw-quals-2013/misc/network1-50

```
file networking.pcap

strings -a networking.pcap | sort | uniq
```

# google-ctf-2016 : no-big-deal-50

```
strings no-big-deal.pcap| egrep ".{10,}" | head 
```

# google-ctf-2016 : no-big-deal-part-2-250(難)

>* https://github.com/amelkiy/write-ups/tree/master/GoogleCTF-2016/NoBigDeal2[有附題目]

# Internetwache-CTF-2016:Network Forensic(MUST)


# CSAW Quals CTF 2013: Networking 2



# picoCTF 2017 : digital-camouflage-50

>* [PicoCTF 2017 - Digital Camoflage Walkthrough](https://www.youtube.com/watch?v=2Zs5zrTEdxk)

```
http.request.method=="POST "
```

Base64 Encoding


# PicoCTF_2017: Special Agent User(MUST)
```
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/34.0.1847.137 Safari/4E423F
```
# BITSCTF 2017 : ghost-in-the-machine-60


# PicoCTF 2013: Second Contact

>* https://github.com/ctfs/write-ups-2013/tree/master/pico-ctf-2013/second-contact

# Insomni'hack Teaser 2017 : {the-great-escape-part1-50}


# hitcon-2017:Data & Mining


# NetworkForensics_10:DNS(難)

>* 33c3 CTF : exfil-100
>* https://github.com/zbetcheckin/33C3_CTF_2k16  ==> 使用 tshark
>* https://0xd13a.github.io/ctfs/33c3/exfil/
```
import base64
import struct
import dpkt
import sys

# packet sequence numbers that we will keep track of
sseq = -1 
dseq = -1 

def decode_b32(s):
    s = s.upper()
    for i in range(10):
        try:
            return base64.b32decode(s)
        except:
            s += b'='
    raise ValueError('Invalid base32')

def parse(name):
    # split payload data at periods, remove the top 
    # level domain name, and decode the data
    data = decode_b32(b''.join(name.split('.')[:-2]))
    (conn_id, seq, ack) = struct.unpack('<HHH', data[:6])
    return (seq, data[6:])

def handle(val, port):
    global sseq, dseq
    (seq,data) = parse(val)

    # remove empty packets
    if len(data) == 0:
        return

    #remove duplicates
    if port == 53:
        if sseq < seq:
            sseq = seq
        else:
            return
    else:
        if dseq < seq:
            dseq = seq
        else:
            return
    sys.stdout.write(data)

# main execution loop - go through all DNS packets, 
# decode payloads and dump them to the screen
for ts, pkt in dpkt.pcap.Reader(open('dump.pcap','r')):
    eth = dpkt.ethernet.Ethernet(pkt)
    if eth.type == dpkt.ethernet.ETH_TYPE_IP:
        ip = eth.data
        if ip.p == dpkt.ip.IP_PROTO_UDP:
            udp = ip.data
            
            dns = dpkt.dns.DNS(udp.data)

            # extract commands from CNAME records and 
            # output from queries
            if udp.sport == 53: 
                for rr in dns.an:
                    if rr.type == dpkt.dns.DNS_CNAME:
                        handle(rr.cname, udp.sport)
            else:
                if dns.opcode == dpkt.dns.DNS_QUERY:
                    handle(dns.qd[0].name, udp.sport)
```
# google-ctf-2016 : for2-200
>* https://github.com/ctfs/write-ups-2016/tree/master/google-ctf-2016/forensics/for2-200
>* https://www.rootusers.com/google-ctf-2016-forensic-for2-write-up/

#  google-ctf-2016 : in-recorded-conversation-25
>* https://github.com/ctfs/write-ups-2016/tree/master/google-ctf-2016/forensics/in-recorded-conversation-25
>* https://fadec0d3.blogspot.tw/2016/05/google-ctf-2016-various-no-big-deal-pt.html
```
tshark -r irc.pcap -T fields -e data 2>/dev/null | python -c "import sys; a=sys.stdin.read().split('\n'); a=[x.decode('hex') for x in a]; a=[x for x in a if 'PRIVMSG' in x and '~' not in x]; print a" | tr ',' '\n' | grep #ctf | tail -n 8 | head -n 7 | sed 's/.*://g;s/\\.*//g' | tr '\n' ' ' | sed 's/ //g'
```
# google-ctf-2016 : magic-code-250

>* https://github.com/ctfs/write-ups-2016/tree/master/google-ctf-2016/forensics/magic-code-250
>* https://fadec0d3.blogspot.tw/2016/05/google-ctf-2016-magic-codes-250.html


 # Internetwache CTF 2016/Misc 70 - Rock With The Wired Shark
>* HTTP Basic Authorization header
 >* https://github.com/bl4de/ctf/blob/master/2016/internetwache_2016/RockWithTheShark_Misc70_writeup.md
 >* https://github.com/raccoons-team/ctf/tree/master/2016-02-20-internetwache-ctf/misc70

 # Internetwache CTF 2016 : Quick Run
>* https://github.com/ctfs/write-ups-2016/tree/master/internetwache-ctf-2016/misc/quick-run-60
>* https://www.xil.se/post/internetwache-2016-misc-60-arturo182/
``` 
cat README.txt | base64 -d > out
```
24 ASCII QR Codes

用手機掃  QR Codes就可以得到答案


 # Internetwache CTF 2016/Misc 50 - The Hidden Message
 >* https://github.com/ctfs/write-ups-2016/tree/master/internetwache-ctf-2016/misc/the-hidden-message-50
 >* https://github.com/p4-team/ctf/tree/master/2016-02-20-internetwache/misc_50
 >* https://poning.me/2016/02/23/the-hidden-message/
``` 
from base64 import b64decode

with open('README.TXT') as f:
    lines = f.read().split('\n')

string = ''
for l in lines[:-2]:
    for byte in l.split()[1:]:
        string += chr(int(byte, 8))

print 'octal to ASCII:'
print repr(string)
print
print 'base64 decode:'
print repr(b64decode(string))
```

```
import base64
print base64.b64decode("".
        join([chr(int(x, 8)) for x in open("README.txt").read().split(" ")]))
```
