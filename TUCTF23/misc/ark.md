# A.R.K

A.R.K 1 to 3 are all based on the same formula - involving cracking a password with a wordlist with only entries having the given string. This can easily be done with [John the Ripper](https://github.com/openwall/john); it supports all 3 types of files.

A.R.K 1 is an SSH private key, crackable with `ssh2john.py`. The flag is simply the password, as stated.

A.R.K 2 is a KeePassXC database, crackable with `keepass2john`. Once the password is found, the file can be opened in KeePassXC. An entry called `flag` is present in the Recycle Bin, with two entries in its history. Rolling back to the first one will reveal the flag under Additional Attributes.

A.R.K 3 is a macOS keychain file, crackable with `keychain2john.py`. Once cracked it can be opened as normal in the macOS Keychain Access utility.

A.R.K 4 is an archive of a Firefox profile. You can simply create a new Firefox profile pointing to the extracted archive, and directly view the password in `about:logins`.