# SELENIUM-PYTHON

![](https://github.com/nu11secur1ty/SELENIUM-PYTHON/blob/main/Docs/Python-Selenium.png)

Selenium for Python 3.x is a very powerful hacking software for websites and web applications.
Also, this software is perfect for the building of exploits and Penetration Testing.

## Example of login to a webpage:

```python
#!/usr/bin/python
# by nu11secur1ty
import time
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By


class Browser:
    browser, service = None, None

    # Initialise the webdriver with the path to chromedriver.exe
    def __init__(self, driver: str):
        self.service = Service(driver)
        self.browser = webdriver.Chrome(service=self.service)

    def open_page(self, url: str):
        self.browser.get(url)

    def close_browser(self):
        self.browser.close()

    def add_input(self, by: By, value: str, text: str):
        field = self.browser.find_element(by=by, value=value)
        field.send_keys(text)
        time.sleep(1)

    def click_button(self, by: By, value: str):
        button = self.browser.find_element(by=by, value=value)
        button.click()
        time.sleep(1)

    def login_linkedin(self, username: str, password: str):
        self.add_input(by=By.NAME, value='username', text=username)
        self.add_input(by=By.NAME, value='password', text=password)
        self.click_button(by=By.CLASS_NAME, value='btn.btn-primary.btn-flat.btn-sm')


if __name__ == '__main__':
    browser = Browser("chromedriver")

    browser.open_page('http://localhost/leave_system/admin/login.php')
    time.sleep(3)

    browser.login_linkedin(username='admin', password='admin123')
    time.sleep(10)

    browser.close_browser()
```
