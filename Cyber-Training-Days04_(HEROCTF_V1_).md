#Cyber-Security Training
#j3kyll
#PATH :~/Vidéos/Hyd3-100Days/Ted_2.0/Security-Advanced/V? heroctf/HeroCTF_v1/crypto

I-CRYPTO

In crypto (here i speak a base switch) don't think that the only base than can be  used for encoding text is 64base 
others base exist  
Ex:
*32base
Ex:
text_cypher: ` O5UG6X3VONSXGX3CMFZWKMZSL4YTCMI=`
CLI_answer:`echo "O5UG6X3VONSXGX3CMFZWKMZSL4YTCMI=" |base32 -d`


*multitap-abc-cipher

plus simply:
The Multi-tap code is the name given to the input technique consisting of writing a letter by repeating the corresponding key on the mobile phone keypad. Example: '2' for 'A', '22' for 'B', '222' for 'C', '3' for D, etc. Similarly 'CODE' is written '222-666-3-33'. dCode has a tool for that

Ex:
`7 444 222 55 88 7 8 44 33 7 44 666 66 33 `

I decripte with dcode(https://www.dcode.fr/multitap-abc-cipher)
R:PICKUPTHEPHONE  *by default all character is a upper*

*16base
In the text encoding the author can would fuck you and he insert the fake code in the good code 
Ex:64cad3cbfabb5b6edbebbk7b93776a53b (here you see that 'k' isn't in hexadecimal)

*md5decrypt

Re-ex:
64cad3cbfabb5b6edbebb7b93776a53b 
you decrypt with (https://md5decrypt.net/)


*RSA (when private key we is given )

file given :
~.flag.enc
&&
~.privkey.pem

you can used openssl inthe case:

cli_openssl:
`openssl rsautl -decrypt -inkey privkey.pem -in flag.enc -out result ` 
` cat result` 
read man openssl

*RSA (middle shit) here  n and e are given
*Tool:RsaCtfTool (https://github.com/Ganapati/RsaCtfTool)*
` for i in `cat rsa2.enc`;do python RsaCtfTool.py -n 627585038806247 -e 65537 --uncipher $i;done` 

*Brainfuck
Ex:
++++++++++[>+>+++>+++++++>++++++++++<<<<-]>>>>---.+++++++.-------.+++++++.-------.+++++++.---------.+++++++++.-------.+++++++++++++++++.--------------.-----.++++++++++++++++.+++.-------------------.+++++++++++++++.+.+++++. 

 dcode always dcode(https://www.dcode.fr/langage-brainfuck)
 
out:
` ahahah_hard_or_not `




































