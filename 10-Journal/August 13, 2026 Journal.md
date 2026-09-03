#journal 


### **1. Cyber Security**
Today I finished the **31. Drive-by Download** and **32. Session Hijacking** lessons which means I completed the **Section 5: Cyber Attacks** section

#### **31. Drive-by Download**
#### 1. What is a Drive-By Download?

A **drive-by download** is a sneaky attack where your device gets infected with malware just because you **visited a compromised website**.

- **The Big Difference:** In most scams, you have to click a link or download a file. In this attack, you don't have to click, download, or interact with anything for the infection to start.

#### 2. How the Attack Works (The Silent Process)

1. **The Setup:** An attacker hides malicious code on a website.
2. **The Visit:** You visit the site normally. You won't see any warnings.
3. **The Scan:** The malicious code quietly scans your computer, browser, and plugins (like your PDF reader) to find **unpatched vulnerabilities** (security "holes" that haven't been fixed yet).
4. **The Infection:** If it finds a hole, it automatically installs a **payload**, such as ransomware, spyware, or a keylogger.

#### 3. What is Malvertising?

Attackers often use **malvertising** (malicious advertising) to spread these attacks. They place infected ads on popular websites. In 2016, even trusted sites like the **New York Times** and **BBC** unknowingly showed malicious ads that could infect visitors.

#### 4. How to Protect Yourself

- **Update Everything:** This is your #1 defense. Regularly update your browser, apps, and operating system to "patch" the holes hackers look for.
- **Use an Ad Blocker:** Since many attacks hide in ads, a good ad blocker stops the malicious code from ever loading on your screen.
- **Security Software:** Keep your antivirus active to catch and block suspicious behavior.
- **Delete Old Junk:** Remove browser plugins or extensions you no longer use, as they can become "open doors" for hackers.

#### **32. Session Hijacking**
#### 1. What is Session Hijacking?

When you log into a website, the site gives you a **session cookie** (or session ID). Think of this like a "VIP Wristband" at a concert—once you have it, you don't have to show your ID (your password) every time you want to go to the bar or the stage.

**Session Hijacking** is when an attacker steals that "wristband" and wears it themselves to impersonate you.

#### 2. Why It’s Dangerous

The scariest part of this attack is that the hacker **does not need your password**. Because the website already "trusts" the session ID, it assumes the person holding it is the legitimate owner of the account.

#### 3. How They Steal Your "Wristband"

Hackers use several methods to grab your session information:

- **Malware:** You might download a file that secretly scans your browser for cookies.
- **Cross-Site Scripting (XSS):** A hacker puts malicious code onto a website that "grabs" your cookies while you're browsing.
- **Unsecured Wi-Fi:** If you use public Wi-Fi that isn't encrypted, hackers can "sniff" the air and catch your data as it travels.
- **Predicting IDs:** If a website is poorly made, a hacker might be able to guess what the next session ID number will be.

#### 4. Real-World Example: Linus Tech Tips (2023)

The famous YouTube channel _Linus Tech Tips_ was hacked this way.

1. An attacker sent a **fake sponsorship email** with a malicious PDF.
2. When an employee opened the file, malware stole their YouTube session cookies.
3. The attacker used those cookies to take control of the channel without ever needing to know the password.

#### 5. How to Stay Safe

- **Use HTTPS:** Only use websites that use encryption (look for the "lock" icon) to protect your connection.
- **Log Out:** When you log out, your "wristband" becomes invalid, so even if a hacker steals it later, it won't work.
- **VPN on Public Wi-Fi:** Use a VPN to hide your traffic if you must use a public network.
- **Clear Cookies:** If you use a shared or public computer, always clear your browser cookies before leaving.


I also did a quiz on **31. Drive-by Download**


I also did quiz on **32. Session Hijacking**


### **2. Django**
I finished working on orders and started working on payment. I also [[What is `reverse()`|learned]] what is `reverse()` for in views, forms, or templates.

- `reverse()` is a Django utility function (from `django.urls`) that takes the **name** of a URL pattern and gives you back the actual **URL path string** for it.

- Think of it like a phone contact list: instead of remembering someone's phone number (the raw URL, like `/accounts/login/`), you just look up their name (`"users:login"`) and Django hands you the number.

```python
from django.urls import reverse

url = reverse("main:product")
# url might be "/products/"
```