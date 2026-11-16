# BDD scenarios using Gherkin

## Feature 1: Calendar Web Component

```gherkin
Feature: Calendar Component
  As user, I want to select a date so I can set it for any purpose

    Rule: Correct opening and closing of dropdowns    
     Background:
      Given the calendar component is rendered

      Scenario: Opening of calendar
        When I interact with the date input
        Then the calendar grid is visible
        And I should see the current month and year at the header
        And I should see the consecutive days for the whole month
        And the starting day of the week should be Monday
    
      Scenario: Closing of calendar by clicking outside
        Given the calendar grid is visible
        When I click outside the calendar grid
        Then the calendar grid hides

      Scenario: Closing of calendar by selecting date
        Given the calendar grid is visible
        When I select a day of the calendar grid
        Then the calendar grid hides
        And the selected date is shown in format "dd/mm/yyyy" in the date input 
        And the delete-date button is visible
      
      Scenario: Opening of year list
        Given the calendar grid is visible
        When I interact with the year
        Then the year list dropdown is visible
        And the list is ordered chronologically 
        And the list shows from 1980 until the current year
        
      Scenario: Closing of year list by selecting year
        Given the calendar grid is visible
        And the year list dropdown is visible
        When I select a year
        Then the year list dropdown hides
        And the selected year is shown at the top header

      Scenario: Closing of year list by clicking outside
        Given the calendar grid is visible
        And the year list dropdown is visible
        When I click on a blank space inside the calendar
        Then the year list dropdown hides
      
      Scenario: Opening of month list
        Given the calendar grid is visible
        When I interact with the month abbreviation
        Then the month list dropdown is visible
        And the list shows the 12 months ordered chronologically
    
      Scenario: Closing of month list by selecting a month
        Given the calendar grid is visible
        And the month list dropdown is visible
        When I select a month
        Then the month list dropdown hides  
        And the selected month is shown at the top header

      Scenario: Closing of month list by clicking outside
        Given the calendar grid is visible
        And the month list dropdown is visible
        When I click on a blank space inside the calendar
        Then the month list dropdown hides  
        And the selected month is shown at the top header

    Rule: Component configurations and disabled states work correctly 
      Scenario: Disabled weekends
       Given the calendar component is configured with disabled weekends
       And the calendar grid is visible
       When I interact with the weekend days
       Then nothing happens
       And the weekend days should be marked in grey
      
      Scenario: Disabled date input
        Given the calendar date input is disabled
        When I interact with the date input
        Then nothing happens
        And the calendar grid should not be visible   
 
    Scenario: Delete date button functionality
      Given the calendar component is rendered
      And a date is selected 
      And the date is visible in the date input
      When I interact with the delete button
      Then the date is deleted
      And the date input shows the placeholder
      And the delete button is hidden

    Rule: Forward and backward navigation buttons allow going through the different months
     Background: 
        Given the calendar component is rendered
        And the calendar grid is visible
      
      Scenario: Forward button makes the next month visible
        When I interact with the going-forward button
        Then the next month is visible
        And the current month hides
        And the month header shows the updated month
        And the year header shows the updated year
     
      Scenario: Backward button makes the previous month visible
        When I interact with the going-backward button
        Then the previous month is visible
        And the current month hides
        And the month header shows the updated month
        And the year header shows the updated year

    Rule: Minimum and maximum dates restrict available selections
      Background:
        Given the calendar component is rendered
        And a minimum date is set as "01/10/2026"
        And a maximum date is set as "16/10/2026"
        
          Scenario Outline: Selecting invalid dates outside limits
            When I select <invalid_date> in the calendar
            Then nothing happens
            And the calendar grid is still visible
            And the selected date is not updated
        
            Examples:
            |invalid_date|
            |30/09/2026|
            |17/10/2026|
  
          Scenario Outline: Selecting valid dates within the boundaries
            When I select <valid_date> in the calendar
            Then the calendar grid hides
            And the selected date is shown in format "dd/mm/yyyy" in the date input
        
            Examples:
            |valid_date|
            |01/10/2026|
            |16/10/2026|

    Rule: Selected/hover dates are highlighted in a unique style  
     Background:
        Given the calendar component is rendered

         Scenario: Highlight of selected date
           Given a date has been selected
           When I open the calendar grid
           Then the selected date is highlighted in a unique style
    
         Scenario: Highlight of hover date
           Given the calendar grid is visible
           When I hover over the different days
           Then they are highlighted in a unique style
        
    Scenario: Date manual typing
      Given the calendar grid is open
      When I write manually a date in the date input
      Then the calendar grid hides
      And the entered date is selected
      And the delete-date button is visible
```
      
--- 

## Feature 2: Checkbox Web Component

```gherkin
Feature: Checkbox Component
  As a user, I want to make choices using checkboxes, so I can select all preferred options.
  
  Rule: Checkbox allows single or multiple selections
    Background:
      Given the checkbox component is rendered

      Scenario: Selecting a checkbox
        Given a checkbox is unchecked
        When I interact with the checkbox or its associated label
        Then the checkbox becomes checked
        And a checkmark or indicator is displayed
  
      Scenario: Deselecting a checkbox
        Given the checkbox is checked
        When I interact with the checkbox or its label
        Then the checkbox becomes unchecked
        And the checkmark is hidden

      Scenario: Checkbox hover
        Given the checkboxes are displayed and unselected
        When I hover over the non-selected checkboxes
        Then those checkboxes become highlighted
        And the cursor changes and indicates the radio button is interactive
  
      Scenario: Disabled checkbox prevents interaction
        Given the checkbox is configured as disabled
        When I attempt to select the checkbox
        Then nothing happens
        And the state of the other checkboxes remains unchanged
```
---

## Feature 3: Lemon Tools Pricing

```gherkin
Feature: Lemon Tools Pricing
  As a user, I want to see the updated prices depending on the selected plan and duration, so that I can compare them and take an informed decision before the purchase. 

  Background:
    Given the user is in the pricing section
    And the duration selector is visible and interacive
    And the duration selector shows the associated discounts
    And the available plans are visible

    Scenario: Baseline prices for 1 month 
      When I mark the option "1 month" from the duration selector
      Then the baseline prices for one month with no discount are visible for each plan
      And no descriptive text is added

    Scenario: Price update for different plan durations
      When I mark the option of a plan duration higher than 1 month
      Then the monthly prices for each plan are updated with the applied discount
      And the regular price is still visible 
      And the regular price is crossed out and reduced
      And a descriptive text is added showing the total cost of the plan
```
---

## Feature 4: Lemon Tools Register

```gherkin
Feature: Lemon Tools Register
  As an unregistered user, I want to register with my own account, so that I can buy the product and manage my plan.

  Background: 
    Given the user is in the register section
    And the username, email, password and password confirmation fields are available

    Scenario: Successfull register using valid credentials
      When I introduce a valid username that does not exist
      And I introduce a valid email that is not already used 
      And I set a valid and secure password
      And I confirm the password correctly
      And I press "Create Account"
      Then the system process the register succesfully
      And the system sends a verification email to the email associated to the new account
 
    Scenario: Username is not valid
      When I introduce a username that does not reach the minimum character length
      Then the system prompts a warning message indicating the requirements
      And the username field is highlighted
      And the new account cannot be created

   Scenario: Email is not valid
      When I introduce an email that does not meet the requirements
      Then the system prompts a warning message indicating the email format is invalid
      And the email field is highlighted
      And the new account cannot be created

    Scenario: Already used username
      When I introduce a username that is already used by another user
      And I introduce a valid email
      And I introduce a valid password
      And I confirm the password
      And I press "Create Account"
      Then the system fails to process the register
      And the system prompts a warning message indicating that username cannot be used
      
    Scenario: Already used email
      When I introduce a valid username
      And I introduce an email that is already used by another user
      And I introduce a valid password
      And I confirm the password
      And I press "Create Account"
      Then the system fails to process the register
      And the system prompts a warning message indicating that email is already in use

    Scenario: Passwords do not match
      When I introduce a valid username
      And I introduce a valid email
      And I introduce a valid password
      And I introduce a different password confirmation
      Then the system prompts a warning message indicating the passwords do not match below the password confirmation field
      And the password confirmation field is highlighted
      And the new account cannot be created
    
    Scenario: Password does not meet security requirements
      When I introduce a valid username
      And I introduce a valid email
      And I introduce a password that does not reach the minimum character length
      Then the system prompts a warning message indicating the password must meet the length requirement below the password field
      And the password field is highlighted
      And the new account cannot be created

    
