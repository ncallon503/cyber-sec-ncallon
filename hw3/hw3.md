# Nathan Callon, 4/30/2024, Intro to Security

## Room 1 completion using hashcat:

```sh
sudo hashcat -m 0 -a 0 -o pass.txt hash1.txt rockyou.txt
```

Password: easy

![hashcat 1](image.png)

```sh
sudo hashcat -m 100 -a 0 -o pass2.txt hash2.txt rockyou.txt
```

Password: password123

![hashcat 2](image-1.png)

```sh
sudo hashcat -m 1400 -a 0 -o pass3.txt hash3.txt rockyou.txt
```

Password: letmein

![hashcat 3](image-2.png)

```sh
sudo hashcat -m 3200 -a 0 -o pass4.txt hash4.txt rockyou_4.txt
```

Made rockyou_4 file with only 4 character words to increase speed.

Password: bleh

![hashcat 4](image-3.png)

```sh
sudo hashcat -m 900 -a 0 -o pass5.txt hash5.txt rockyou.txt
```

Password: Eternity22

![hashcat 5](image-4.png)

Had to use hashid for this to find that this was a SHA-256.

```sh
sudo hashcat -m 900 -a 0 -o pass6.txt hash6.txt rockyou.txt
```

Password: paule

![hashcat 6](image-5.png)

```sh
sudo hashcat -m 1000 -a 0 -o pass7.txt hash7.txt rockyou.txt
```

Password: n63umy8lkf4i

![hashcat 7](image-6.png)

```sh
sudo hashcat -m 1800 -a 0 -o pass8.txt hash8.txt rockyou.txt
```

Password: waka99

![hashcat 8](image-7.png)

```sh
sudo hashcat -m 160 -a 0 -o pass9.txt hash9.txt rockyou.txt
```

Password: 481616481616

![hashcat 9](image-8.png)

![Room #1 completion](image-9.png)

![TryHackMe profile](image-10.png)

## Using john instead of hashcat:

hash 1: 48bb6e862e54f2a795ffc4e541caed4d

```sh
john --format=raw-md5 --wordlist=rockyou.txt hash1.txt
```

hash 2: CBFDAC6008F9CAB4083784CBD1874F76618D2A97

```sh
john --format=raw-sha1 --wordlist=rockyou.txt hash2.txt
```

hash 3: 1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032

```sh
john --format=raw-sha256 --wordlist=rockyou.txt hash3.txt
```

hash 4: $2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom

```sh
john --format=bcrypt --wordlist=rockyou.txt hash4.txt
```

hash 5: 279412f945939ba78ce0758d3fd83daa

```sh
john --format=raw-md4 --wordlist=rockyou.txt hash5.txt
```

hash 6: F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85

```sh
john --format=raw-sha256 --wordlist=rockyou.txt hash6.txt
```

hash 7: 1DFECA0C002AE40B8619ECF94819CC1B

```sh
john --format=nt --wordlist=rockyou.txt hash7.txt
```

hash 8: $6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.

```sh
john --format=sha512crypt --wordlist=rockyou.txt hash8.txt
```

hash 9: e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme

```sh
john --format=raw-sha1 --wordlist=rockyou.txt hash9.txt
```

## Awk script, passphrases and cracking

I used the command listed:

```sh
sudo awk -f sample.awk -v n=20 /usr/share/wordlists/rockyou.txt > rockyou20.txt
```

With sudo permissions to create rockyou20.txt file with 20 entries.

![awk 1](image-11.png)

![awk 2](image-12.png)

I then used the command:

```sh
sudo awk -f sample.awk -v n=3 rockyou20.txt > 3lines.txt
```

to generate a 3lines.txt file with these contents:

![awk 3](image-13.png)

Formatted the newlines into spaces:

![awk 4](image-14.png)

I then generated a key using these 3 words as the passphrase:

```sh
ssh-keygen -t ed25519
```

```sh
troyangel1 jaw3594773 0853139926
```

![awk 5](image-16.png)

I cd'ed to ~/.ssh and ran the command:

```sh
python3 /usr/share/john/ssh2john.py id_ed25519
```

to convert it into a format john can understand.

![awk 6](image-17.png)
