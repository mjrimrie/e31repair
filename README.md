

Convert all htm files to html: 
- `find . -name "*.htm" -exec sh -c 'mv "$1" "${1%.htm}.html"' _ {} \;`

Update all html files to reference html not htm
- `find . -type f -exec sed -i.bak "s|\.htm/|.html|g" {} \;`

Update all html files to reference s3 bucket for images for:
1. extra/htm
`find . -type f -exec sed -i.bak "s|...images/|https://<s3_buckname>.s3-us-west-2.amazonaws.com/images/extra/|g" {} \;`

2. tdata/htm
`find . -type f -exec sed -i.bak "s|...images/|https://<s3_buckname>.s3-us-west-2.amazonaws.com/images/tdata/|g" {} \;`

3. repair/htm
`find . -type f -exec sed -i.bak "s|...images/|https://<s3_buckname>.s3-us-west-2.amazonaws.com/images/repair/|g" {} \;`

4. torque/htm
`find . -type f -exec sed -i.bak "s|...images/|https://<s3_buckname>.s3-us-west-2.amazonaws.com/images/torque/|g" {} \;`