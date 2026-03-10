**Broken Access Control** is the number one vulnerability in the **OWASP Top 10 for 2025** and is considered one of the most critical web security flaws.

**Access control** is simply the set of rules that define user roles. For example, a visitor can view the homepage but cannot access the admin page—and of course, the admin is the one who can see that page. But imagine if a regular user could become an admin and view the admin page. This brings us to the **Broken Access Control** vulnerability.

It occurs when the application fails to enforce the role-based rules we just mentioned, usually due to a flaw in how roles are verified on the server.

Let's take a very simple example to explain this:

`/profile?id=2`

Here we have a simple parameter sent to the server to say, "I am the user with ID 2, please get my profile page." The server responds with, "Sure, here's the page," without any verification. The problem arises if the ID is changed, and the server actually fetches and displays another user's page—information that a regular user shouldn't see.

**So, where is the mistake?**  
The mistake is that the server trusts the user's input blindly. If the user says "my ID is 2," the server says "OK." If the user says "100," it says "OK." If the user enters any ID belonging to another user, the server just complies.

**Types of Broken Access Control:**

- **IDOR (Insecure Direct Object Reference)** – This is the most common type. Let’s take an example: You are downloading a file from a website—let’s say an invoice. The parameter might look like this: `/download?invoice_2.pdf`. If you change the number and access another user's invoice, that's IDOR.

- **Vertical Privilege Escalation** – This simply allows a regular user to act as an admin. For example, a URL like `/admin/delete_user`—if a normal user opens this link and deletes a user, they are performing an action with admin privileges. That’s a vulnerability.

- **Horizontal Privilege Escalation** – This allows a user to access another user's data. For example, you are a regular user but can view the data of a different regular user.

- **Forced Browsing** – This means you can access hidden pages, such as the admin panel, just by knowing the URL.

**How to Fix These Vulnerabilities:**  
There are many ways to fix them, the most important being:
- Never trust user input; always validate and verify on the **server side**, not the frontend.
- Use **UUIDs** instead of numeric IDs. A UUID looks something like this: `a8f7c9e1-33b4-4f21`. However, this is not a complete protection on its own.

**In summary:**  
The vulnerability occurs when a user is able to access something they should not be able to access.
