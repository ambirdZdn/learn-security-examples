# Privilege Escalation

The example demonstrates a privilege escalation vulnerability and how to exploit it.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, send a GET request

    ```
        http://localhost:3000/send-form
    ```

4. Try different UserIds and see which one gives you authorized access to change the role of that user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
    No session management, no validation of new user role, no protection of unauthorized role modification.

2. Briefly explain how a malicious attacker can exploit them.
    a. Anyone can make request due to lack of session verification, so easily modift any user roles like elevating privileges to administor.
    b. No authorization check so attackers can impersonate any user by using their id. 

3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?
    Add a sseion middleware with authentiction check and role updates, which allows track logged-in users, and check their roles, ensuring only authenticated users' access and verifying requesters has admin level of provileges. 