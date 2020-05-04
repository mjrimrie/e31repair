


The file structure of the Repair CD is

```
cd-root folder
	| - images
	| - en 
		| - extra 
			| - images
			| - html
		| - images
		| - repair
			| - images
			| - html
		| - torque
			| - images
			| - html
		| - tdata
			| - images
			| - html
```

### 1. Move all images to a spearate folder in the root folder:
```
cd-root folder
	| - en
	| - images
		| - extra
		| - repair
		| - root
		| - torque
		| - tdata
```

The `images/root` folder are all those images in `cd-root folder/images` and in `cd-root/en/images/`

### 2. Update all the html files to point to the new image folder, or where the images are to be hosted (ex. S3)
- extra/htm
`find . -type f -exec sed -i.bak "s|...images/|https://<s3_buckname>.s3-us-west-2.amazonaws.com/images/extra/|g" {} \;`

- tdata/htm
`find . -type f -exec sed -i.bak "s|...images/|https://<s3_buckname>.s3-us-west-2.amazonaws.com/images/tdata/|g" {} \;`

- repair/htm
`find . -type f -exec sed -i.bak "s|...images/|https://<s3_buckname>.s3-us-west-2.amazonaws.com/images/repair/|g" {} \;`

- torque/htm
`find . -type f -exec sed -i.bak "s|...images/|https://<s3_buckname>.s3-us-west-2.amazonaws.com/images/torque/|g" {} \;`

### 3. Convert all the htm files to the html suffix
Convert all htm files to html: 
- `find . -name "*.htm" -exec sh -c 'mv "$1" "${1%.htm}.html"' _ {} \;`

### 4. Update all html files to reference html not htm
- `find . -type f -exec sed -i.bak "s|\.htm/|.html|g" {} \;`

