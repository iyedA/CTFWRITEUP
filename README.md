# Headache Extravaganza {NSFK}ids

## Description : 
This is a miscellanious local ctf competition in our group mainly focusing on cryptography and contains one flag at the end which you get a part each time you progress a bit.
To solve this you need good skills in cryptography decoding and a lot of patience... A LOT.

## Starting the challenge:
The information you get for this CTF is as follows:
![Données](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_231836206.png)<br>
Before i start, i want to say that i may skip some strings because they are rabbitholes / a waste of time!
Now the most interesting detail other than the prizes is:
```
A+B = Key To Start Chall(e)nge!
```
Hence explaining that both links have a relationship with one another. So we open both of them together to see these two:
![A](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_231916812.png)<br>
![B](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_231942483.png)<br>
Now page *A* is just a password submitting page which contains useful informations for later on, but in order to find the password we need to do some digging.<br>
We could read the hint mentioning %d and \d then studying about them, but we're not pussies that take hints and so instead we focus on page *B*.
Remember that we were told to not move and try what we see. Thus first thing to do is to look around until we see this:
![Ambulance??](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_232015151.png)<br>
Now how often do you see an ambulance in a gas station? That's definitely something important! Especially the number...
And indeed, the number is our password through, which takes us to this page:
![Entered A](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_232056111.png)<br>
which points towards a text channel in our discord server with a weird name...
## And so we begin!
![Big Brain Idea](https://github.com/iyedA/CTFWRITEUP/blob/assets/neuron%20activation.jpg)<br>
Now if your neurons activated like me, you would copy paste that name in cyberchef (The famous cyber swiss army knife) and try ol' reliable ROT13 decoding, which sure enough works right away to tell us:
```
from-imed-xd-sanity-check-passed-so-welcome-to-the-maze-be-ready-for-the-rabbit-holes
```
We should also mention that the description has a link shaped first string, the second half of it looks familiar, almost like a youtube URL... So we try replacing the domain with youtube and tld with .com
![](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_232309761.png)<br>
Interesting gameplay but an even more interesting description. After putting it in cyberchef for it to magic wand it we get:
```
oaawz://fvbab.il/IvXOXKRTr9H
```
Doesn't that look like a link? We ROT13 it as always to get a functioning https link leading to another youtube video...
![](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_232431343.png)<br>
Same as always, cyberchef magic wands it from base64 to give us what looks like a paragraph but distorted with special characters like "@", "[", ":"... ROT13 wouldn't work on these, but ROT47 will!
![](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_232535237.png)<br>
Amazing! we got our first part of the flag, we just need to *cybercook* it. We know it needs XOR and a base decoding.<br>
If you ask me, that looks like a hex, and so we from hex it then xor... But we need a key! except we have the output and the input, we can discover the key.<br>
We know the flag format starts with "flag{". So we switch the key from hex to UTF8 and type in flag{. Which gives us 1337, a key!
![](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_232625090.png)<br>
Now back to the video to watch the editing skills and decode the rest of its cryptography, we get a hint from the second string in the description.
```
Shouldn't the title's first encrypted part be in the end?
```
Aha! now we go to cyberchef to reverse it and ROT13..<br>
Now it's telling us to find where the email should be. Must be the "about" channel section!
![](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_232722275.png)<br>
After joining the server with the encrypted link by decoding it through base64>ROT47>ROT13, we enter an empty server.<br>
But we get an interesting role which gives us a link to another server!<br>
![](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_232828178.png)<br>
This one has a useful encrypted base64 and ROT13 hint telling us to send xanax a friend request (do it) and checking his about me section.
![](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_232854532.png)<br>
We see he has a key role with the name "freexanax", don't forget about it! But we also see 2 links, one encrypted and another getting us to:
```
https://pastebin.com/qw2NyF4r
```
In this website xanax thanks us for being a good friend and gives us an encrypted ROT47>ROT13>URL Decode youtube link.. But this one doesn't get us anywhere..!<br>
Until you notice the last part of it contains:
```
M4K35_
```
Well believe it or not, you already got the second part of the flag! Now we have:
```
flag{pr4c71c3_M4K35_
```
You know what they say, "Practice Makes Perfect". So let's keep working!
Back to the encrypted link Xanax typed in his description.. We go to cyberchef it with Vigenère Decode. But you may ask "We don't have a key!"
![](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_233036147.png)<br>
Remember the key role i told you about!?
And so we get this link:
```
https://www.youtube.com/shorts/ezc2rz2cz0E
```
Huh, it's just a meme !
But wait, did you check the description?
![](https://github.com/iyedA/CTFWRITEUP/blob/assets/image_2023-07-28_233055127.png)<br>
There we go! Just by reading that you get 5 points out of 15 to get a reward if you show Imed how you got here!
