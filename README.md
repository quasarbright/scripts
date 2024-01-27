# scripts

shell scripts I find useful

# create-encrypted, edit-encrypted
These two scripts are used to create and edit password-protected files.

example:
```
$ create-encrypted secret.md
```
enter a password and then once vim opens, type some secret stuff in the file and then save and exit. this will create `secret.md.gpg`.
```
$ edit-encrypted secret.md.gpg
```
enter the password and then once vim opens, edit your secret stuff in the file and then save and exit. this will edit `secret.md.gpg`

The unencrypted text only ever exists in a temporary file that gets deleted once the editing is done. (the temporary file is created in `/tmp` as per `maketemp`.

# zip-and-encrypt, decrypt-and-unzip

These two scripts are used to manage password-protected directories.

For example:

```
$ mkdir secrets
$ echo "i like popcorn" > secrets/secret.md
$ zip-and-encrypt secrets
$ rm -rf secrets
```
This creates `secrets.tar.gz.gpg`, which is password-protected.

```
$ decrypt-and-unzip secrets.tar.gz.gpg
```
This gives you back `secrets/` once you enter the password. The workflow is storing the encrypted zip, decrypting and unzipping it, editing it, zipping and encrypting it, and then storing that. 
