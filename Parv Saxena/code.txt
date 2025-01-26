from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Set up the WebDriver
driver = webdriver.Chrome()  # Make sure you have chromedriver installed
driver.get("https://www.google.com")

# Find the search box element
search_box = driver.find_element(By.NAME, "q")

# Type the search query and hit Enter
search_query = "Python programming"
search_box.send_keys(search_query)
search_box.send_keys(Keys.RETURN)

# Wait for the results to load
time.sleep(2)

# Scrape the search results
search_results = driver.find_elements(By.CSS_SELECTOR, 'h3')

# Print the titles of the search results
for result in search_results:
    print(result.text)

# Close the browser
driver.quit()
