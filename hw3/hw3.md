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
