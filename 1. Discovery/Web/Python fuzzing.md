```
# Import the libraries we downloaded earlier
# if you try importing without installing them, this step will fail
from bs4 import BeautifulSoup
import requests 

# replace testurl.com with the url you want to use.
# requests.get downloads the webpage and stores it as a variable
for i in range (0,50):
	num = (2*i) +1
	html = requests.get(f'http://10.10.115.11/api/{num}') 
	print( html.text)

```