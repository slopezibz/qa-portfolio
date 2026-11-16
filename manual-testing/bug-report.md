# Bug Reports
## Bug Report 1

| **Bug ID** | `UIL-10` |
| **Project** | UI library - Calendar Component |
| **Title** | Dates can be selected out of a defined range |
| **Severity** | Medium |
| **Priority** | High - Date selection impacts many workflows |
| **Environment** | Windows 11 Pro | Google Chrome |
| **Reported by** | Sara L.I.|
| **Date** | 17/08/2026 |

---

### Details
Dates that are outside the limits of a previously defined date range can be selected anyway.

---

### Steps to reproduce
1. Define 1/08/2026 as minimum date.

2. Define 31/08/2026 as maximum date.

3. Interact with date input → the calendar opens.

4. Check whether the dates outside the selected range (steps 1 and 2) are available to select.

---
### Expected result
August 2026 is the only month available to select a date. The rest of the dates are disabled. 

---
### Actual result
All dates are available, independently of the predefined minimum and maximum. 

---

## Bug Report 2

| **Bug ID** | `UIL-44` |
| **Project** | UI library - Checkbox Component |
| **Title** | No animation is showed when hovering a selectable checkbox |
| **Severity** | Low |
| **Priority** | Low |
| **Environment** | Windows 11 Pro | Google Chrome |
| **Reported by** | Sara L.I.|
| **Date** | 20/10/2026 |

---

### Details
Cursor does not change nor any animation is showed to indicate that a checkbox is selectable.

---
### Expected result
When any checkbox is selectable, the cursor changes and an animation is showed when hovering to indicate the interactivity. 

---
### Actual result
No cursor change and no animation is showed upon hovering over any selectable checkbox.  

---

## Bug Report 3

| **Bug ID** | `WEB-9` |
| **Project** | Lemon Tools Webpage - Pricing |
| **Title** | Relocate plan and discount boxes |
| **Severity** | Low - It does not affect correct functioning of purchase flow |
| **Priority** | High - High visual impact that affects user experience exploring the webpage|
| **Environment** | Desktop Firefox (Windows 11)| Chrome for Android (Google Pixel 8 and Samsung Galaxy)|
| **Reported by** | Sara L.I.|
| **Date** | 02/03/2026 |

---

### Details
Depending on the device used and screen size, plan and discount boxes are overlapped differently, in some cases difficulting readability. This section needs to be redesigned to be adaptive. 

---

## Bug Report 4

| **Bug ID** | `WEB-15` |
| **Project** | Lemon Tools Webpage - Register |
| **Title** | Invalid captcha when registering |
| **Severity** | High - Blocking user registering flow |
| **Priority** | High |
| **Environment** | Desktop Firefox (Windows 11)| Chrome for Android (Google Pixel 8)|
| **Reported by** | Sara L.I.|
| **Date** | 02/03/2026 |

---

### Details
A message indicating "Invalid Captcha" is shown when registering any user.

---

### Steps to reproduce
1. Enter the webpage https:\\lemonrotools.com.

2. Go to "Register".

3. Fill in all the fields with valid credentials (username, email, password and confirmation password).

4. Press "Create Account".


---
### Expected result
The system process the registration succesfully and sends a verification email. A notification appears indicating that: "Account created, check your email". 

---
### Actual result
A warning message appears: "Invalid Captcha" and the system fails to process the registration. 

---