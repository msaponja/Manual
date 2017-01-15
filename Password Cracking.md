# Password Cracking [[3]]

## John The Ripper - JTR

###JTR password cracking

	john --wordlist=/usr/share/wordlists/rockyou.txt hashes	
	
### JTR forced descrypt cracking with wordlist

	john --format=descrypt --wordlist /usr/share/wordlists/rockyou.txt hash.txt
	

### JTR forced descrypt cracking with wordlist

	john --format=descrypt hash --show
	
[3]: <https://highon.coffee/blog/penetration-testing-tools-cheat-sheet/#john-the-ripper---jtr>