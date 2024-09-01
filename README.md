# Cicada IITBHU
_Fresher's digital treasure hunt by COPS_
Writeup by GEN1U5

### 1. The Discord Video
**Difficulty:** Noob, **Tags:** Reverse, Stego

**Correct Path:**
- A video was shared in the official COPS infosec server. <video controls src="https://i.imgur.com/AdNVH7q.mp4" title="Title"></video> Video with audio -> https://i.imgur.com/AdNVH7q.mp4
- The quote _"life is lived forward but judged in reverse lol"_ could be seen. When we try to hear what is being said in the video, it can be observed that the audio has been reversed (as suggested by the quote too). So the audio can be extracted and reversed using online software [extractor](https://audio-extractor.net), [reverser](https://mp3cut.net/reverse-audio).
- The reversed audio talks about a COC clan and tells that the clan name can be found in one of the discord server's admin's discord info. 
- Upon investigation, we can conclude that admin ***inspectorchingum*** has the discord info "_P4yl04d P1r4t35_" which is the name of a COC clan as told by the reversed audio. 

**Red Herrings:**
- The quote or its author had no signifigance other than the word ***reversed*** used in the quote.
- There was one more admin (***Wizard***) on the discord server with the discord info set as a clan code (***#2GJLPCRYR***). The name of this clan is ***Kings of COC***. The wasy to avoid this was to listen the audio carefully, it talks about the name and not the code.

### 2. The COC Clan
**Difficulty:** Easy, **Tags:** Web, Crypto

**Correct Path:**
- After getting the clan name, you can search for the clan on [online clan searchers](https://clashspot.net/en/clans/search). 
In the clan description, we notice 2 things:
    1. a word/phrase with some asterisks (***s\*\*\*\*\*\*emes***)
    2. a gibberish string (possibly a cipher)

- The next clue lies in the clan description which contains a ciphered string ***9EEADi\^\^HHH\]C655:E\]4@>\^C\^:?7\_;\_<bC0DBFc5\^***. 
- We can use cipher analysers present on the internet to identify the cipher, for example [dcode.fr](https://dcode.fr/cipher-identifier). From here, we find that the cipher used is ROT47. To decrypt the ROT47, this [tool](https://www.dcode.fr/rot-47-cipher) can be used.
- Upon decrypting we find the [link](https://www.reddit.com/r/inf0j0k3r_squ4d/) to a subreddit called ***inf0j0k3r_squ4d***. This is the next clue. It matches the description of the clan too, as the word with asterisks would stand for _"share memes"_ and reddit is a famous place for such things. Also, reddit is place where we can remain anonymous (usually) as told by the description too.

**Red Herrings:**
- Unrelated messsages sent by some participants of the hunt also worked as unintentional diversions for some other participants. For example, the mention of ***Spiritrun*** on the clan chat spread like wildfire among participants and distracted a lot of people. The way to avoid this was to ignore the COC chat messages from newly joined clan members. _This remained a very big diversion throughout the hunt for a lot of participants._

### 3. The *inf0j0k3r_squ4d* subreddit
**Difficulty:** Hard, **Tags:** Analysis, Crypto, Brute Force, (Stego, if red herring is followed)

**Correct Path:**
- In the subreddit, we can see there we numerous memes posted base on the genre of tech and cybersec in general. Most of these were unrelated. To find the one that contained the clue, we check the posts made by the subreddit Moderator (***u/Staowolin***). We see 2 posts: (one of which is a red herring, explained in the next section)
    1. The first post titled ***"let us all come together!"*** had an image attached to it. ![first post](https://i.redd.it/qaj0qoysbcld1.png)
    We can clearly see 2 sticky note windows open and one of them has the name of a book by a famous author. The other one has 3 youtube links.
    2. The second post titled ***"join me in my journey to topple X"*** contains the [link](https://x.com/iHateElon12Now) to a twitter account serving as a divergence.

- The links in the first post when typed, seemed to be broken and the YouTube videos couldn't be found.
The clue lies in the video ID but not the links themselves. When the video IDs are concatenated together in the order they are given (i.e. ***IGh0dHBzOi8vcGFz + dGViaW4uY29tL3Uv + VDM3aDNybTRuYzNy***) we can clearly see a base64 string which can be easily decoded using online decoders like [this](https://base64decode.org/).
- This gives us the next clue which is a pastebin user's profile link [https://pastebin.com/u/T37h3rm4nc3r](https://pastebin.com/u/T37h3rm4nc3r).

**Red Herrings:**
- There were a lot of other memes and posts on the subreddit that were not posted by the moderator, these could distract participants from focussing on the important post. The way to avoid this was to only focus on the posts by the moderator, as the community was public, anyone could post anything.
- The twitter link was also a major red herring. It did have some suspicious posts regarding the true message of a meme hidden inside it. This could distract users into thinking about steganography and the metadata of the numerous images encountered in this challenge.
- The image also contained another sticky note open which had the name of the book and its author. Some participants also got diverted in that direction.
- The final major red herring of this challenge wasthe barely visible outline of a country on the second image. (a high contrast image of the map has been attached) ![Map outline](https://i.imgur.com/SP9BX8B.png) A lot of participants interpreted it as a country's outline. Some even tried to use the VPN of the outlined country to open the YouTube links.

### 4. The pastebin link
**Difficulty:** Easy, **Tags:** Analysis, Crypto, Search

**Correct Path:**
- The pastebin user has two pastes on the website:
    1. secret 
    2. Busy God

- The first paste requires a password. The second paste descirbes the password. It has a poem from a book and the name of the book in a certain format (also mentioned in the paste) is the password. 
- The name of the book is **"The God of Peace"** and so the password for the paste is ***THE_GOD_OF_PEACE***. It can be easily found by simple google searches and a little bit of bruteforcing. 
- Now, the **secret** paste contains another cipher. The cipher can be identified using online tools like [this one](https://dcode.fr/cipher-identifier). It uses ***Brainfuck*** cipher. Decrypting the cipher using online tools like [this one](https://www.dcode.fr/brainfuck-language) gives us the link to a GitHub repository (***NotReadyToCommit*** by ***Argus817***) [https://github.com/Argus817/NotReadyToCommit](https://github.com/Argus817/NotReadyToCommit), which is the next clue.

**Red Herrings:** No major red herrings in this challenge.

### 5. The GitHub repository
**Difficulty:** V. Hard, **Tags:** Analysis, Crypto, Forensics

**Correct Path:**
This challenge can be divided into 3 major parts: <br>
**1. Understanding what to find and what to do**
- Reading the ***"README\.md"*** file in the repo gives us the basic idea. We have an encrypted image and we need to decrypt it by creating a decryption algorithm.
- The algorithm can be made by reverse engineering the ***encrypt*** function in ***script\.py*** present in the same repo.
- Decryption should give us an image with the name ***location\.png*** which is our next clue.
<br>

**2. Finding Key and IV**
- Reading the code in script\.py, we realize that to decrypt we need two very important things, a Key and an IV for the AES256 encryption both of whose lenght is 16 bytes.
- The first thing to notice in GitHub is the ***commit history*** of the file script\.py. We can find a total of 13 commits almost all of which have different keys and IVs. We can make a list of possible keys from here. This list can be shortened by checking which keys are actually 16 bytes long.
- Reading the encrypt function we see that the ***return value*** of the function is ***iv + ciphertext***
```python
def encrypt(plaintext, key, iv):
    padded = pad(plaintext, 16)
    cipher = AES.new(key, AES.MODE_CBC, iv)
    ciphertext = cipher.encrypt(padded)
    return iv+ciphertext
```
- This must mean that the encrypted\.png file contains both the iv and the ciphertext concatenated together. Finally, the IV can be interpreted as the first 16 bytes of encrypted\.png and rest of the bytes are of the encrypted image which must be decrypted. These bytes can be extracted using online Hex Editors like [hexed.it](https://hexed.it).
- The key can now be bruteforced out of the list after we have written the decryption algorithm. 
<br>

**3. Writing the decryption algorithm**
- The decrypt function is nothing but the ***inverse function of encrypt***. The input parameters can be ciphertext, key and IV.
- The ciphertext needs to be decrypted using the inbuilt ***decrypt*** method of the cipher class created using the AES module, the key and the IV to get the padded text.
- The padded text can be unpadded using the inbuilt ***unpad*** function and padding size 16 (devised from the encrypt function)
```python
def decrypt(ciphertext, key, iv):
    cipher = AES.new(key, AES.MODE_CBC, iv)
    padded = cipher.decrypt(ciphertext)
    unpadded = unpad(padded, 16)
    return unpadded
```
- Now the main function can be re-written to ***read encrypted data from encrypted.png*** and ***write decrypted data into location.png***.
*(Here encrypted.png is the file with the first 16 bytes removed.)
```python
def main():
    with open('encrypted.png','rb') as file:
        data = file.read()
    decData = decrypt(data, KEY, IV)
    with open('location.png', 'wb') as decFile:
        decFile.write(decData)
```
- If everything is done correctly, this should give the output as location.png image. ![location.png](https://i.imgur.com/QmJaaWE.png) This is our next clue.

**Red Herrings:** No major red herrings in this challenge. The path was pretty straightforward with the correct tools, knowledge, skillset and a keen eye for details.

#### 5. The Binary & The IRL QRs
**Difficulty:** Medium, **Tags:** Crypto, Touching grass

**Correct Path:**
- The image location.png contains binary data separated by bytes. The binary can be easily converted to ASCII using online tools like [this one](https://www.rapidtables.com/convert/number/binary-to-ascii.html).
- The ASCII value gives us 3 co-ordinates. These are 3 different locations in the IITBHU campus.
    1. **25°15'41.6"N 82°59'32.8"E** -> G11 Electrical Dept.
    2. **25°15'33.9"N 82°59'36.1"E** -> SBI Branch
    3. **25°15'41.3"N 82°59'22.2"E** -> SDP Library

Upon reaching these locations IRL, one would search for QRs and scan them. The locations 1 and 3 were **Red Herrings** and their QRs pointed to **Rickrolls**.
<video controls src="https://i.imgur.com/PBQWZPe.mp4" title="Title"></video>

The QR near the SBI Branch was valid and pointed to a google form which was ***THE FINAL STEP***.
## This was CICADA IITBHU
(atleast the conventional way 🫣) *\*smirks\**

### Bonus: Loopholes and workarounds.
- The first hint from the video told us to search for info of the admins of the Discord server. During this, the name **Argus817** came in front of us.
- Google searching the admin name ***directly*** brings us to challenge #4 and no previous knowledge (of challs 1, 2 and 3) is required to find the coordinates. (although answers of all 5 challs are asked in the google form and are important to find in order to win the hunt.)
##### This is the way our team followed. After we had the locations in our hand, we then further found the conventional way to reach the GitHub repo too. 😉 
