# Automation-Table-Testing
### Code
```
from selenium import webdriver
from selenium.webdriver.common.by import By
import re

driver = webdriver.Chrome()
driver.get("https://assertqa.com/practice/webtables")

driver.implicitly_wait(10)

table = driver.find_element(By.TAG_NAME, "table")

headers = table.find_elements(By.TAG_NAME, "th")
rows = table.find_elements(By.CSS_SELECTOR, "tbody tr")

print("\nTC01 - Print All Column Headings")
for h in headers:
    print(h.text)

print("\nTC02 - Print First Data Row")
print(rows[0].text)

print("\nTC03 - Print Last Data Row")
print(rows[-1].text)

print("\nTC04 - Search Employee by Last Name")
search = driver.find_element(By.XPATH, "//input[@type='search']")
search.send_keys("Smith")
print(table.text)

print("\nTC05 - Extract All Email Addresses")
emails = re.findall(r'[\w.-]+@[\w.-]+\.\w+', table.text)
for email in emails:
    print(email)

print("\nTC06 - Employee with Highest Due Amount")
print("Due column is not available in this table.")

print("\nTC07 - Verify Website Link Exists")
links = driver.find_elements(By.TAG_NAME, "a")
found = False

for link in links:
    if "assertqa.com" in link.get_attribute("href"):
        found = True
        break

if found:
    print("PASS - Website link exists")
else:
    print("FAIL - Website link not found")

print("\nTC08 - Count Data Rows")
print("Total rows:", len(rows))

driver.quit()
```
### Output
<img width="1268" height="971" alt="image" src="https://github.com/user-attachments/assets/77ca2a88-30ae-4377-a0b8-fe099c673776" />
<img width="1273" height="717" alt="image" src="https://github.com/user-attachments/assets/a8f7aee8-13ec-4312-be40-0e6d02d2612b" />
<img width="873" height="802" alt="image" src="https://github.com/user-attachments/assets/4a920394-564f-4b73-ade9-31870f097a7f" />
<img width="885" height="313" alt="image" src="https://github.com/user-attachments/assets/16bb32db-1906-41a1-b4d1-c2a369e29274" />
