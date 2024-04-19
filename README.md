# memlabs
## LAB 1
first I installed volatility plugin on my pc after reading through the lab 0 readme file on memelabs github page.
![image](https://github.com/adwait3/memlabs/assets/148553626/c2860169-2e94-475f-b5ef-33044e584e01)

then i used pslist to get the data of the running processes at the time of system crash
![Screenshot from 2024-04-19 15-33-11](https://github.com/adwait3/memlabs/assets/148553626/513ed18b-f0c5-4e60-a973-3ca0c3822d03)

while looking at these processes i find 3 interesting ones (which arent running in the background normally)
namely cmd, ms paint and winrar
then i use concole to check their details 

![Screenshot from 2024-04-19 16-18-41](https://github.com/adwait3/memlabs/assets/148553626/71126044-6ddd-4ee0-be02-9a9be0c70e8b)

i find this                                                                                 
C:\Users\SmartNet>St4G3$1                                                       
ZmxhZ3t0aDFzXzFzX3RoM18xc3Rfc3Q0ZzMhIX0=    
this is base 64
![Screenshot from 2024-04-19 16-21-22](https://github.com/adwait3/memlabs/assets/148553626/2260ae93-4414-4e4e-87e4-733846e8feb0)

i get the first flag
flag{th1s_1s_th3_1st_st4g3!!}

now we see mspaint
using memdump plugin we get the memory dump i used . to ge tin the current directory
now we rename the file to 2424.data
i googled a bit on how to open this file and found that gimp can be used so i downloaded gimp using sudo apt and used it 
![Screenshot from 2024-04-19 16-46-04](https://github.com/adwait3/memlabs/assets/148553626/4e314a31-2b12-4ac2-a706-ed585cfd2a4d)
this looked very werid so i played around with the features trying different things
i changed the height to 800 and width to 3280 and then flipped the image vertically to find this 
![Screenshot from 2024-04-19 16-59-34](https://github.com/adwait3/memlabs/assets/148553626/7d5f1b65-2650-4f48-8ea9-9be4708b0396)
tis gav eme the second flag 
flag{G00d_Boy_good_girL}

now for the third winrar we use cmdline to see what was happeneing 
![Screenshot from 2024-04-19 18-55-49](https://github.com/adwait3/memlabs/assets/148553626/cac936f7-797b-4a17-8323-90aec2590eae)
we find this very importnat file now we use filescan to get to that file 
![Screenshot from 2024-04-19 19-05-47](https://github.com/adwait3/memlabs/assets/148553626/53e7eec3-7e41-4104-a64d-ff7bb9a4826b)
we use dumpfiles to get the file and now get a file named file.None.0xfffffa8001034450.dat we change it to important.rar
now we unrar it 
![Screenshot from 2024-04-19 19-15-57](https://github.com/adwait3/memlabs/assets/148553626/cd39b0f9-6cd9-44b3-b106-aa559437ecc7)
but we see that this file is password protected 
to get the password we use hashdump
![Screenshot from 2024-04-19 19-20-15](https://github.com/adwait3/memlabs/assets/148553626/beb1f6b9-6969-4bc8-af52-a52ba6be149c)
we see the alisa simpson hash and get it
f4ff64c8baac57d22f22edc681055ba6
convert to upper case and get the flag
![Screenshot from 2024-04-19 19-28-21](https://github.com/adwait3/memlabs/assets/148553626/68da182f-e412-4423-803d-57f315aabb90)
and we get the third flag
flag{w3ll_3rd_stage_was_easy}
