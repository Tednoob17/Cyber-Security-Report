#Cyber-Security Training
#j3kyll
#PATH :~/Vidéos/Hyd3-100Days/Ted_2.0/Security-Advanced/JEI-CTF-master/

## ANALYSE AND RECEIVED KNOWLEDGES

## 
1-PATH:/home/j3kyll/Vidéos/Hyd3-100Days/Ted_2.0/Security-Advanced/JEI-CTF-master/Prequals

If you get the pcap files start with the filtrage (dns or ftp)
See 👀 the sections 'infos' and you observe the good informations

With the ftp server if you want connect in the server to do:

~FTP

*ftp $(ip_adress)
if you login and one answers on server is "Remote system type is UNIX."
So the (CLI) Linux walk and you would search your files and i precise use all command who would help you 👷
And if you want download the file on the server :
` get $(file_name)` 

2-
~DNS
See well the filtrage answers and search one address web 
Ex: ^www ,$.com ,$.fr or others country registry

👀 Use your ultra-vision for search the file or name_file encoded


3-
~STEGANOGRAPHIE
First reaction front off pictures in a ctf is a using tool:
A-`strings ` so you can see the flag (it's mode easy)👻
B-` binwalk`  or ` foremost` :for see if you can extract one things on picture 
C-`git `:if the file as been changed on the branch and rest with the default or new changment
D-
IF you receive one file contains the words in incredible langage (fourchelangue langage) etc .... 
Verify if the  end of message containe "=" or "==" <- it's possible that the base64
While the file decode contains "=" he is always encoded in base64
Ex:
Message Encoded:||L|1U|vM|i8|x|L1||cv||||Y|y|9|G|L0|Uve|i9V|L20|vMS|9ZL|00v|My|9|OL24||vVS||9X||L3Qv|Qi9NL|2svN|S9H|L08vWC|9|S|L1|IvUy|9FL|zAve||i|9|UL|1Q||v|Ti9|K|L|1|o|v|M|i|9|a|L|1|I|v|U|C|9|U|L|z|A|v|P|Q|=|=

#PYTHON FOR FUCKS THIS LANGAGE

`
>>> string="||L|1U|vM|i8|x|L1||cv||||Y|y|9|G|L0|Uve|i9V|L20|vMS|9ZL|00v|My|9|OL24||vVS||9X||L3Qv|Qi9NL|2svN|S9H|L08vWC|9|S|L1|IvUy|9FL|zAve||i|9|UL|1Q||v|Ti9|K|L|1|o|v|M|i|9|a|L|1|I|v|U|C|9|U|L|z|A|v|P|Q|=|="


>>> string=string.replace('|','')


>>> base64.b64decode(string)

b'/U/2/1/W/c/F/E/z/U/m/1/Y/M/3/N/n/U/W/t/B/M/k/5/G/O/X/R/R/S/E/0/z/T/T/N/J/Z/2/Z/R/P/T/0/='

>>> string="/U/2/1/W/c/F/E/z/U/m/1/Y/M/3/N/n/U/W/t/B/M/k/5/G/O/X/R/R/S/E/0/z/T/T/N/J/Z/2/Z/R/P/T/0/="

>>> string=string.replace('/','')

>>> base64.b64decode(string)

b'SmVpQ3RmX3sgQkA2NF9tQHM3M3IgfQ=='


>>> string="'SmVpQ3RmX3sgQkA2NF9tQHM3M3IgfQ=='"

>>> base64.b64decode(string)

b'JeiCtf_{ B@64_m@s73r }'

>>> exit()

`














































