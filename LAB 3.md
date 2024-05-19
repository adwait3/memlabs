# LAB 3
## part ono
first we chcek the active processses using 

```
python3 vol.py -f '/home/kali/Desktop/MemoryDump_Lab3.raw' windows.pslist
```
![pslist](https://github.com/adwait3/memlabs/assets/148553626/f064b55d-ab79-41b7-9bf9-12af638f3a76)

we see notepad is active so now we use 
```
python3 vol.py -f '/home/kali/Desktop/MemoryDump_Lab3.raw' windows.cmdline
```
to see the command line processes and find notepad we see 'evilscript.py' and 'vip.txt' were being used so we try to dump these processes.

![cmdline](https://github.com/adwait3/memlabs/assets/148553626/a2b61aef-c4a6-4236-bed2-9e2dc4954196)

first we scan for these processes using 
```
python3 vol.py -f '/home/kali/Desktop/MemoryDump_Lab3.raw' windows.filescan | egrep "evilscript.py|vip.txt"
```
![grep](https://github.com/adwait3/memlabs/assets/148553626/aa64b750-68a0-4ffd-b0d7-f0a0d0b4b131)


now we dump these files using 
```
python3 vol.py -f '/home/kali/Desktop/MemoryDump_Lab3.raw' -o "/home/kali/Desktop" windows.dumpfiles --physaddr 0x3de1b5f0
python3 vol.py -f '/home/kali/Desktop/MemoryDump_Lab3.raw' -o "/home/kali/Desktop" windows.dumpfiles --physaddr 0x3e727e50 
```

![dump](https://github.com/adwait3/memlabs/assets/148553626/f6f8d9e4-56c5-489b-9c09-b25748676a1b)


![py](https://github.com/adwait3/memlabs/assets/148553626/565ceae9-080c-485b-b08d-4d5441d80bd9)

we get a text from vip 'am1gd2V4M20wXGs3b2U='
and a python file with code 
```
import sys
import string

def xor(s):

        a = ''.join(chr(ord(i)^3) for i in s)
        return a


def encoder(x):

        return x.encode("base64")


if __name__ == "__main__":

        f = open("C:\\Users\\hello\\Desktop\\vip.txt", "w")

        arr = sys.argv[1]

        arr = encoder(xor(arr))

        f.write(arr)

        f.close()
```

we see that this file is XORing the code with 3 and base 64 ing it then strong it in VIP as the  text we got so we can reverse it to get the original text

![Screenshot 2024-05-19 173324](https://github.com/adwait3/memlabs/assets/148553626/3cdd2853-0201-4118-918a-2b43767917c6)
atfer this we get first half of the flag which is 

'inctf{0n3_h4lf'

## part 2

for the second part of the flag
