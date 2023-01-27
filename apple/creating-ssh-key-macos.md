## Creating a SSH key on macOS

Something I learned a long time ago, but I seem to forget every time I need it.

The command to generate a SSH key is:

```bash
ssh-keygen -t rsa
```

If you want to copy the public key on your clip board, use following command:

```bash
cat [name-of-your-ssh-file].pub | pbcopy
```

