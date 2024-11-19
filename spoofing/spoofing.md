# Spoofing

This example demonstrates spoofind through two ways -- Stealing cookies programmatically and cross site request forgery (CSRF).

## Steps to reproduce the vulnerability

1. Install dependencies

    `$ npx install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. Start the malicious server **mal.ts**

    `npx ts-node mal.ts`

4. Open __http://localhost:8000__ in a browser, type a name and Submit.

5. Open the __Application__ tab in the Browser's inspect pane. Find the __Cookies__ under __Storage__. You should see a __connect.sid__ cookie being set.

6. Open the HTML file __mal-steal-cookie.html__ file in the same browser (different tab). Open inspect and view the console.

7. Click the link in the HTML file. Do you see the cookie being stolen in the console?

8. Open the HTML file __mal-csrf.html__ file in the same browser (different tab). What do you see if the user has not logged out of **insecure.ts**? What do you see if the user has logged out? 


## For you to answer

1. Briefly explain the spoofing vulnerability in **insecure.ts**.
    In the middleware to create session part, it uses cookie: { httpOnly: false } and no sameSite cookie protection, making it accessible via JS client code, so might causing Cross-site Request Forgery (CSRF) and Session hijacking.

2. Briefly explain different ways in which vulnerability can be exploited.
    a. Cookie access by JS, accessing document.cookie and logging it.
    b. CSRF: No protection is implemented so malicious site can excute in user's session like changing user info without their knowledge.

3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.
    Because it modify cookie setting:
    a. httpOnly: true, which prevents JS access to the cookies
    b. sameSite: true, which ask cookies onlt sent to first-party context, avoiding CSRF attack