- Execution Policy
`Get-ExecutionPolicy -list`
Execution policies can have seven different values;
	1.  AllSigned: Scripts can run but require all scripts to be signed by a trusted publisher.
	2.  Bypass: All scripts can run, and no warnings or prompts will be displayed.
	3.  Default: This refers to “restricted” for Windows clients and “RemoteSigned” for Windows servers.
	4.  RemoteSigned: Scripts can run, and this does not require local scripts to be digitally signed.
	5.  Restricted: The default configuration for Windows clients. Allows individual commands to run, does not allow scripts.
	6.  Undefined: This shows that no specific execution policy was set. This means default execution policies will be enforced.
	7.  Unrestricted: Most scripts will run.