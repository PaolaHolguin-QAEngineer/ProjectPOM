# Automated Testing Project: Urban Routes

## Project Overview
This project involves creating and executing automated tests for the **Urban Routes** application. The goal is to verify the proper functionality of the application by simulating common user behaviors, such as data entry and option selection, throughout the user flow.

## Exercises

### Exercise 1: Combining Methods into One Step

**Objective**:  
To understand how to combine multiple methods into a single method, streamlining the testing process.

**Instructions**:  
You are given multiple methods to simulate user actions, such as filling in an email field, password field, and clicking the login button. Instead of repeating these actions in multiple tests, you need to create a new method that combines them into one seamless step.

1. **Existing Methods**:  
   - `set_email()` – fills the email field.  
   - `set_password()` – fills the password field.  
   - `click_sign_in_button()` – clicks the sign-in button.

2. **Create a new method `login()`, combining all three**:  
```python
def login(self, email, password):
    self.set_email(email)
    self.set_password(password)
    self.click_sign_in_button()

# Exercise 2: Create a Step for the Registration Page

## Objective:
Create a step that automates the entire user registration process, combining the actions of filling in the email, password fields, and clicking the register button into one method.

## Instructions:

1. Define the necessary locators for the registration page.
2. Implement the methods `set_email`, `set_password`, and `click_registration_button`.
3. Combine them into a method `register()`.

### Python Code Example:

```python
def register(self, email, password):
    self.set_email(email)
    self.set_password(password)
    self.click_registration_button()

# Exercise 3: Validate the Occupation Field

## Objective:
Write an automated test to validate the **Occupation** text field on the main page.

## Instructions:

1. Store the value from the **Occupation** field into a variable `description`.
2. Verify that the value is correctly stored using an assertion.

### Python Code Example:

```python
description = self.driver.find_element(*self.occupation_field).text
assert description == "Expected Occupation"

# Exercise 4: Validate Email Display in Header After Login

## Objective:
After logging in, verify that the user's email appears in the header of the main page.

## Instructions:

1. Create a page object for the header and define the element required.
2. Use the login method created earlier and a new method to verify that the email is correctly displayed in the header.

### Python Code Example:

```python
email = "user@example.com"
header_page = HeaderPageAround(self.driver)
assert header_page.email_text.text == email

# Exercise 5: Verify the Login Process with Multiple User Accounts

## Objective:
Automate the process of testing the login functionality with multiple user accounts.

## Instructions:

1. Use a list of user credentials and iterate through them.
2. For each account, use the `login()` method to log in and verify that the correct user is logged in by checking the header.

### Python Code Example:

```python
user_credentials = [("user1@example.com", "password1"), ("user2@example.com", "password2")]

for email, password in user_credentials:
    self.login(email, password)
    header_page = HeaderPageAround(self.driver)
    assert header_page.email_text.text == email


