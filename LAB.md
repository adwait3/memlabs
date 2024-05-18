## LAB 2
# installing volatility3
for this level i decided to use volatility 3 on my kali vm , Installing volatility three was not as straightforward as expected i folllowed the following steps

`git clone https://github.com/volatilityfoundation/volatility3.git`

then cd to the directory

```
cd volatility3
sudo python setup.py install
python3 vol.py --h
/usr/bin/python3 -m pip install --upgrade pip
pip3 install -r requirements.txt
```

after this your volatilty 3 setup is complete and you can start using the plugins for solving the level

## First part

``python3 vol.py -h``

use this to see the different plugins and their uses.
first i used

``python3 vol.py -f '/home/kali/Desktop/MemoryDump_Lab2.raw' windows.info``

to view the info and found it was windows 7 machine


![Screenshot 2024-03-18 100617](https://github.com/adwait3/memlabs/assets/148553626/c41159bb-0975-4f90-98ba-7a03f9237a06)
after this i used

``python3 vol.py -f MemoryDump_Lab2.raw windows.pslist.PsList``

to see the processes
![pslist](https://github.com/adwait3/memlabs/assets/148553626/82052238-034f-46be-9c13-f8d41f964f0a)

afer this i used 

``python3 vol.py -f MemoryDump_Lab2.raw windows.envars``

to see the environment variables
![variablespng](https://github.com/adwait3/memlabs/assets/148553626/0905da9f-478f-49c3-8d8d-79ca8beef071)

and found temp c variable with some fishy looking stuff (``ZmxhZ3t3M2xjMG0zX1QwXyRUNGczXyFfT2ZfTDRCXzJ9``) put it on cyber chef to get the first flag

``flag{w3lc0m3_T0_$T4g3_!_Of_L4B_2}``

## part two
for part two we use file scann 

```
python3 vol.py -f MemoryDump_Lab2.raw -profile=Win7SP1x64 windows.filescan | grep password -i
python3 vol.py -f MemoryDump_Lab2.raw -profile=Win7SP1x64 filescan | grep "Hidden.kdbx"
```

![physcaddr](https://github.com/adwait3/memlabs/assets/148553626/b18e004e-5c80-4a7f-a10a-1e4ac6b63f5d)

now we dump these files using 

```
python3 vol.py -f MemoryDump_Lab2.raw -profile=Win7SP1x64 -o '/home/kali/Desktop'   windows.dumpfiles  --physaddr 0x3fce1c70
python3 vol.py -f MemoryDump_Lab2.raw -profile=Win7SP1x64 -o '/home/kali/Desktop'   windows.dumpfiles  --physaddr 0x3fb112a0
```

to open thw kbdx file we need a software called keepass which can be installed by 
>sudo apt install keepass2


after this we open our kdbx file which prompts for password and we enter our password which we got from the password.png file 

![pass](https://github.com/adwait3/memlabs/assets/148553626/2159e0a3-f83f-463f-8e46-ef045e5ff8e4)

'P4SSw0rd_123'

![key](https://github.com/adwait3/memlabs/assets/148553626/a540ec39-270f-4c3a-92bc-55c0947b2498)

![flag](https://github.com/adwait3/memlabs/assets/148553626/a0913f02-a70d-474b-90cb-76699ff05641)

copying the password gives the second flag 

>flag{w0w_th1s_1s_Th3_SeC0nD_ST4g3_!!}

## part 3

