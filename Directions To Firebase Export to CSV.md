# To Firebase Export to CSV

1. Export the json from the Firebase console
	- You can do this through the console
	- Or export through the `firebase` CLI if you are deploying throught the CLI
2. Move to folder that you are working in
3. Use `jq` to get the key remove top-level dictionary element. *(I am duplicating the key in the object so this is fine to do.)*<br/>
	`< filename.json jq .[] > filename2.json`
4. Check the new file <br/>
	`< filename2.json jq .`
5. Add a comma after every bracket. `json2csv` is throwing an error with out this.<br/>
	`sed 's/}/},/g' filename2.json > filename3.json`
6. Open the file in `vim` and make some tweaks
	1. `vim filename3.json`
	2. type `shift + O` to start editing at the top of the file
	2. Add `[` to the beginning of the file
	3. Press `Esc` then `shift + G + A`
	4. Remove the `,` at the end of the file
	5. Add `]` to the end of the file
	6. Press `Esc` then type `:x` to save changes.
7. Check the new file <br/>
	`< filename3.json jq .`
8. At this point we can convert from `json` to `csv` 
	- You can use `json2csv` if need
	- You can use csvkit's `in2csv` - going to use csvkit for the rest of this.
9. To convert the json to csv
	`in2csv filename3.json >  filename3.csv`
10. To preview the new csv<br/>
	`csvlook filename3.csv | head` - the `head` portion just limits the file to the top 10 lines as preview.
11. At this point it is now a csv. 