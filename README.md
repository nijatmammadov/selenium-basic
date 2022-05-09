# selenium-basic

from selenium import webdriver
import os

from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as ec

os.environ['PATH']+= r"C:\selenium-drivers"
driver = webdriver.Chrome()

driver.get("https://demo.seleniumeasy.com/jquery-download-progress-bar-demo.html")

driver.implicitly_wait(4)

my_element = driver.find_element(by=By.ID , value="downloadButton")

my_element.click()

# progress_element = driver.find_element(by=By.CLASS_NAME,value="progress-label")
# print(f"{progress_element.text=='Completed!'}")

WebDriverWait(driver,30).until(
    ec.text_to_be_present_in_element(
        (By.CLASS_NAME,"progress-label"),
        'Complete!'
    )
)
