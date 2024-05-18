## LAB 2
# installing volatility3
for this level i decided to use volatility 3 on my kali vm , Installing volatility three was not as straightforward as expected i folllowe dthe followng steps 
>git clone https://github.com/volatilityfoundation/volatility3.git
then cd to the directory
>cd volatility3
sudo python setup.py install
python3 vol.py --h
/usr/bin/python3 -m pip install --upgrade pip
pip3 install -r requirements.txt
after this your volatilty 3 setup is complete and you can start using the plugins for solving the level

## First part

'python3 vol.py -h'
use this to see the different plugins and their uses
first i used 
'python3 vol.py -f '/home/kali/Desktop/MemoryDump_Lab2.raw' windows.info'
to view the info and found it was windows 7 machine

![Screenshot 2024-03-18 100617](https://github.com/adwait3/memlabs/assets/148553626/c41159bb-0975-4f90-98ba-7a03f9237a06)
after this i used 
'python3 vol.py -f MemoryDump_Lab2.raw windows.pslist.PsList'
to see the processes
![pslist](https://github.com/adwait3/memlabs/assets/148553626/82052238-034f-46be-9c13-f8d41f964f0a)
afer this i used 
'python3 vol.py -f MemoryDump_Lab2.raw windows.envars'
to see the environment variables
![variablespng](https://github.com/adwait3/memlabs/assets/148553626/0905da9f-478f-49c3-8d8d-79ca8beef071)
and found temp c variable with some fishy looking stuff ("ZmxhZ3t3M2xjMG0zX1QwXyRUNGczXyFfT2ZfTDRCXzJ9") put it on cyber chef to get the first flag

"flag{w3lc0m3_T0_$T4g3_!_Of_L4B_2}"

## part two



