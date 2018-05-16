
>* picoCTF2013: Bitwise
>* https://github.com/ctfs/write-ups-2013/tree/master/pico-ctf-2013/bitwise

題目:
```
#!/usr/bin/env python

user_submitted = raw_input("Enter Password: ")

if len(user_submitted) != 10:
  print "Wrong"
  exit()


verify_arr = [193, 35, 9, 33, 1, 9, 3, 33, 9, 225]
user_arr = []
for char in user_submitted:
  # '<<' is left bit shift
  # '>>' is right bit shift
  # '|' is bit-wise or
  # '^' is bit-wise xor
  # '&' is bit-wise and
  user_arr.append( (((ord(char) << 5) | (ord(char) >> 3)) ^ 111) & 255 )

if (user_arr == verify_arr):
  print "Success"
else:
  print "Wrong"
```

解答1:
```
verify_arr = [193,35,9,33,1,9,3,33,9,225]

password =[0,0,0,0,0,0,0,0,0,0]

for i in range(10):
    for k in range (128):
        if verify_arr[i]==(((k<<5|k>>3)^111)&255):
            password[i]=chr(k)
            break
key=''
for a in password:
    key+=a

print key
```

解答2:
```

```

>* PicoCTF 2013: Byte Code
>* https://github.com/ctfs/write-ups-2013/tree/master/pico-ctf-2013/byte-code
```
import java.io.Console;
import java.io.PrintStream;

class Authenticator
{

    public Authenticator()
    {
    }

    public static void main(String args[])
    {
        key = new char[10];
        key[0] = 'M';
        key[1] = 'Y';
        key[2] = 'T';
        key[3] = 'y';
        key[4] = 'w';
        key[5] = 'x';
        key[6] = 'a';
        key[7] = 'o';
        key[8] = 'h';
        key[9] = 'r';
        Console console = System.console();
        for(String s = ""; !s.equals("ThisIsth3mag1calString7695"); s = console.readLine("Enter password:", new Object[0]));
        for(int i = 0; i < key.length; i++)
            System.out.print(key[i]);

        System.out.println("");
    }

    public static char key[];
}
```
