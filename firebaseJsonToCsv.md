### Code for terminal
```
< filename.json jq .[] > filename2.json
< filename2.json jq .
sed 's/}/},/g' filename2.json > filename3.json
vim filename3.json

```

### ///
### Edit it vim
	1. type `shift + O` to start editing at the top of the file
	2. Add `[` to the beginning of the file
	3. Press `Esc` then `shift + G + A`
	4. Remove the `,` at the end of the file
	5. Add `]` to the end of the file
	6. Press `Esc` then type `:x` to save changes.
### ///

### Code for terminal
```
< filename3.json jq .
in2csv filename3.json >  filename3.csv
csvlook filename3.csv | head

```
