# Signing Commits

```
git config --global commit.gpgsign true
git commit -S -m your_commit_message
# Creates a signed commit
```

# Signed & Verifying Releases

A digital signature certifies and timestamps a file. If the file is subsequently modified in any way, a verification of the signature will fail. A digital signature can serve the same purpose as a hand-written signature with the additional benefit of being tamper-resistant. The GnuPG source distribution, for example, is signed so that users can verify that the source code has not been modified since it was packaged.

To download my signing key, use either one of the methods below. Both commands will download the same key.

```
gpg --keyserver hkp://pgp.mit.edu --recv-keys 8ACD28A5
curl https://keybase.io/randarxj7/key.asc | gpg --import
```

Once you have my key, you can verify files by using the command.
`gpg --verify key.asc file.zip` or `gpg --verify file.zip.sig file.zip`
You should see a message like the following:

```
gpg: Signature made Sat 29 Jul 2017 12:14:18 AM CDT using RSA key ID BE6ED428
gpg: Good signature from "Randy Rowland <rowland007@gmail.com>"
```
You want to see **Good signature**.

# Signing Releases
`gpg --output file.sig --detach-sign file`
or
`gpg -ab file` this will create `file.asc`
If you need to put the signature inside of a text file you can use
`gpg --clearsign file.txt`

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

gpg --keyserver hkp://pgp.mit.edu --recv-keys 8ACD28A5
curl https://keybase.io/randarxj7/key.asc | gpg --import
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1

iQIcBAEBAgAGBQJZfBthAAoJEL/0LvG+btQosIYP/RV1dCEKEbT56HnSx+/vK24J
0VqaUtSZqbb9PWARPL4ji26m0QfxTgbVxXWo8OT0m4vAOS9cRKov7hgZQhbOqC4a
WU/Hso02hsZv/0kMgyor48G4tVehPcPJU4oo3bpAfVJqz/CUOCn0QtU0FPJwFV5M
0wVeeGuHhMXlNhyC++uxiBwwqVFMdL4iO1PijvBGoduxyt/uoBN8q2Z7cQyVI2n6
0PFPShvcU28MZbEaKYv4cRCTBb3OGkA9tteiRtwArN9+QdCYHxwoRos6fFxbt1xi
x6YxprbalwS05Lgrxo7k5OarmUr23WBLMT5KXFUGUJXU9pV9CNvp41W6VpjwT71i
RrjO9BVudjQz6mhn64u6uiBWNmX9VhME7M615eMk1oUpGVKBiYfMLTTiaGyl8QYE
6rdZPWquNXflE2gmBzeYBgjhjOpkNVFdoVSToAZgOLvE2jRNFwa4KuybnPFq5Od+
YGgUELIVockUafttkB4CiBXH2LdahnoHmq8SlgEL8aYb0aI3khqpv0mW5iN/sgja
0oIoNOzK8O4Gf2wM8kugmEvN67mZTyioDrP4Oy3C9DIL7hqjSegrlp95wlZ0CK2y
X/pPjtg5kPfcHbPD47BNiHLo5sh9ItwEhKFq6V/p8+zhO4hCiqRM239wi4FDGvx0
Qog57bj6lHGqzmOHSvX5
=H2Vm
-----END PGP SIGNATURE-----
```
To verify this, you just need to run `gpg --verify keys.asc` This method does not require two files.

----
