## Methodology
1.  Find a file upload point.
2.  Try uploading some innocent files -- what does it accept? (Images, text files, PDFs, etc)
3.  Find the directory containing your uploads.
4.  Try to bypass any filters and upload a reverse shell.
5.  Start a netcat listener to receive the shell
6.  Navigate to the shell in your browser and receive a connection!

- Languages and frameworks
	- Wappalyzer
	- Checking headers
- Find upload page
- View source code for client side filtering
- Innocent file upload
	- Access file
		- Direct access / embedded
		- Naming scheme
		- GoBuster
- Malicious file upload
	- Bypassing client side filters
	- View errors from server side to bypass

## Errors
- testingimage.invalidfilextension
	- server has extension blacklist
		- Upload innocent file but change:
			- Magic number
				- https://en.wikipedia.org/wiki/List_of_file_signatures
			- MIME type (burp)
	- Enumerating file lengths
