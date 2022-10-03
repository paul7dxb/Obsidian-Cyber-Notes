### Navigatin a page
https://selenium-python.readthedocs.io/navigating.html

### Example web navigation and useage
```
from selenium import webdriver
#Lets you use tab enter etc.
from selenium.webdriver.common.keys import Keys
#By for gettielements by id / class etc.
from selenium.webdriver.common.by import By
#Options for Chrome settings like keep login
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.action_chains import ActionChains

from selenium.webdriver.support.ui import Select

import time

import numpy as np

#Establish Chrome
PATH = "/home/kali/MyPrograms/chromedriver"
#driver = webdriver.Chrome(PATH)

#Chrome profile
options = Options()
options.add_argument("user-data-dir=/tmp/tarun")
driver = webdriver.Chrome(options=options, executable_path=PATH)

#Set wait times
driver.implicitly_wait(10)

resultsNumbers = []

taxons = ["Ostrea","Crassostrea","Magallana", "Ostreidae","Oyster*"]


def searchAndDownload(searchTerm):

	#Navigate to search page
	driver.get("https://www.website")
	searchBox = driver.find_element(By.ID,"advancedSearchInputArea")
	#clear search field
	searchBox.clear()
	#Fill in search term and send
	searchBox.send_keys(searchTerm)
	searchBox.send_keys(Keys.RETURN)
	#Results page

	#Catch for if no results
	try:
		#get number of results from class = search-info-title font-size-20 ng-star-inserted
		resultFull = driver.find_element(By.CLASS_NAME,"search-info-title")
	except:
		resultNum = str(0)
		resultsNumbers.append(resultNum)
		print(f'{searchTerm}\t{resultNum}')
	else:
		#Get result number from class = brand-blue
		resultNum = resultFull.find_element(By.CLASS_NAME,"brand-blue")
		print(f'{searchTerm}\t{resultNum.text}')
		resultsNumbers.append(resultNum.text)

		#Select export menu (type app-export-menu)
		exportButton = driver.find_element(By.TAG_NAME,"app-export-menu")
		#Actions driver
		actions = ActionChains(driver)
		actions.move_to_element(exportButton)
		actions.click(exportButton)
		actions.perform()

		#Select export to en desktop (ID exportToEnwDesktopButton)
		actions = ActionChains(driver)
		enDesktop = driver.find_element(By.ID,"exportToEnwDesktopButton")
		actions.move_to_element(enDesktop)
		actions.click(enDesktop)
		actions.perform()

		#Select export (class = mat-focus-indicator cdx-but-md mat-stroked-button mat-button-base mat-primary)
		
		actions = ActionChains(driver)
		enDesktop = driver.find_element(By.CLASS_NAME,"mat-stroked-button")
		actions.move_to_element(enDesktop)
		actions.click(enDesktop)
		actions.perform()
	

searchTerms = []
taxonSearches = []

#Read in searchterms
with open("searchterms.txt") as my_file:
	for line in my_file:
		searchTerms.append(line.rstrip('\n'))

print(searchTerms)
print(len(searchTerms))


for searchTerm in searchTerms:
	for taxon in taxons:
		taxonSearch = searchTerm.replace("taxon", taxon)
		taxonSearch = searchTerm.replace("Taxon", taxon)
		taxonSearches.append(taxonSearch)
		print("starting new search")
		searchAndDownload(taxonSearch)
		#sleep before going to next one
		time.sleep(5)

#Output results
with open('results.txt', 'w') as f:
	for i, taxonSearch in enumerate(taxonSearches):
		f.write(f"{taxonSearch}\t{resultsNumbers[i]}\n")


#All done now quit
driver.quit()
```

Get all HTML:
```
print(driver.page_source)
```