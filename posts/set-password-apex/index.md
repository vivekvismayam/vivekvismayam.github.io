# Programatically Control User Passwords in Apex 🔐


In Salesforce, resetting a user's password is a common admin task — but did you know developers can do it programmatically using Apex?
There are two main methods which a developer need to be aware of!

## Set Password Method 🍭
### 🚀 What is System.setPassword()?
System.setPassword(userId, newPassword) is a static method in the Apex System class that allows you to set a new password for any user, as long as the executing user has necessary permissions.

```Apex
    Id userId = '005XXXXXXXXXXXX'; // Replace with actual User ID
    String newPassword = 'Secure@123';
    System.setPassword(userId, newPassword);
```
### 📕 Important Notes
- The user whose password is being set will not receive the standard "reset password" email.
- If a security question hasn't been previously configured, a user trying to login is redirected to the "Change Your Password" page.
- The password must match the org’s password policies (length, complexity, etc.).
- The method only works in Apex code that runs in system context, like triggers, classes, or anonymous execution in Developer Console.
- It does not work in a sandbox where user identity confirmation is disabled.
>Be careful with this method, and do not expose this functionality to end-users.

### ⚠️ When to Use This?
Here are some practical use cases:  
- 🔄 Migrating users from another system and setting initial passwords.
- 🛠️ Admin utilities built inside the org for internal support teams.

### 🧪 Example: Setting User Password from an Apex Class
```Apex
public class PasswordsetHelper {
    public static void setUserPassword(Id userId, String newPassword) {
        try {
            System.setPassword(userId, newPassword);
            System.debug('Password successfully set for user: ' + userId);
        } catch (Exception e) {
            System.debug('Error resetting password: ' + e.getMessage());
        }
    }
}
```
### ✅ Best Practices
- Always validate the password against your org’s security policies before setting.
- Avoid exposing this method through a public API or unsecured Flow/Apex page.
- Log the operation securely if used in an internal admin tool.
- Use and communicate with caution as we are doing this on behalf of an end user
### 🚫 Common Errors
| Error| Reason|
| ----- |----- |
| `System.InvalidParameterValueException: INVALID_NEW_PASSWORD:`| The new password doesn’t follow org policy |
| `System.InvalidParameterValueException: UNKNOWN_EXCEPTION`    | Invalid repeated password   |
| `System.InvalidParameterValueException: INVALID_USER_ID`      | Invalid or inactive User ID passed in     |
| `System.UnexpectedException: INACTIVE_OWNER_OR_USER`          | Qwner or user is inactive     |
| `System.InvalidParameterValueException: INSUFFICIENT_ACCESS`  | Running user do not have sufficient permissions to complete this operation|


`System.setPassword()` is a powerful Apex method that lets you reset a user’s password programmatically. It’s a useful tool for admins and developers building internal automation — but must be used carefully due to its sensitive nature.  

---
### 📚Salesforce Documentations
- Read More about [`System.setPassword()`)](https://developer.salesforce.com/docs/atlas.en-us.apexref.meta/apexref/apex_methods_system_system.htm#apex_System_System_setPassword) in Salesforce Apex Developer Guide📕
- Read Salesforce [Help Arcticle](https://help.salesforce.com/s/articleView?id=000387826&type=1) about how set password method behaves.
---

## Reset Password Method 🍬

### 🚀 What is System.resetPassword(userId, sendUserEmail)?
resetPassword() is a static method in the Apex System class that lets you reset a user's password and optionally trigger the standard Salesforce password reset email. System.resetPassword(userId, sendUserEmail) offers a flexible and secure way to reset user passwords while giving you control over whether to notify the user. It’s an excellent method for admin support automation, onboarding flows, or maintenance tasks — all while keeping security intact.
```Apex
Id userId = '005XXXXXXXXXXXX'; // Replace with the actual User ID
Boolean sendEmail = true;
System.resetPassword(userId, sendEmail);
```
>- If `sendEmail = true`, the user will get the standard "reset your password" email from Salesforce.
>- If `sendEmail = false`, the password will be reset silently (typically used for automation).

### 📕 Important Notes
- The new password is system-generated and not visible to the developer.
- You can optionally suppress the password reset email by setting `sendUserEmail = false`
- The user must change their password the next time they log in.Users are prompted to enter a new password, and to select a security question and answer if they haven't already
>Be careful with this method, and do not expose this functionality to end-users.

### ⚠️ When to Use This?
- Bulk password resets during migrations or sandbox refreshes.🔁
- Admin console tools built for help desk or support agents.🔧
- Silent resets in testing environments without emailing users.🔕 
- Compliance resets (e.g., force a password reset for selected users) or Adhoc password reset🛡️ 

### 🧪 Example: Reset and Email Notification
```Apex
public class PasswordResetManager {
    public static void resetAndNotify(Id userId) {
        try {
            System.resetPassword(userId, true);
            System.debug('Password reset email sent to user: ' + userId);
        } catch (Exception e) {
            System.debug('Error resetting password: ' + e.getMessage());
        }
    }
}
```
>If you want to reset without sending an email:`System.resetPassword(userId, false);`

### ✅ Best Practices
- Use ```resetPassword()``` over ```setPassword()``` when you don't need to specify the password manually.
- Only suppress the reset email in controlled internal environments.
- Always wrap it in a try-catch block to handle permission or validation errors.

### 🚫 Common Errors
| Error                           | Reason                                      |
| ------------------------------- | ------------------------------------------- |
| `System.InvalidParameterValueException: INVALID_USER_ID`| Invalid or inactive User ID passed in     |
| `System.UnexpectedException: INACTIVE_OWNER_OR_USER`    | Qwner or user is inactive     |
| `System.InvalidParameterValueException: INSUFFICIENT_ACCESS`  | Running user do not have sufficient permissions to complete this operation|


### 📚Salesforce Documentations
- Read More about [`system.resetPassword()`](https://developer.salesforce.com/docs/atlas.en-us.apexref.meta/apexref/apex_methods_system_system.htm#apex_System_System_resetPassword) in Salesforce Apex Developer Guide📕
- Read Salesforce [Help Arcticle](https://help.salesforce.com/s/articleView?id=000387826&type=1) about design.
---

##  Set  vs Reset Password 🥤
| Feature                              | `setPassword()`                         | `resetPassword()`                |
| ------------------------------------ | --------------------------------------- | -------------------------------- |
| Specify password                     | ✅ Yes                                   | ❌ No (system-generated)          |
| Send email                           | ❌ No                                    | ✅ Optional                       |
| Forces password change at next login | ❌ No                                    | ✅ Yes                            |
| Best for                             | Internal tools, setting known passwords | User-friendly resets, automation |
---

>## Reset Password With Email Template 🍫
>`resetPasswordWithEmailTemplate(userId, sendUserEmail, emailTemplateName)`  
>Resets the user's password and sends an email to the user with their new password. You specify the email template that is sent to the specified user. Use this method for external users of Experience Cloud sites.  
>Read More about [`resetPasswordWithEmailTemplate`](https://developer.salesforce.com/docs/atlas.en-us.apexref.meta/apexref/apex_methods_system_system.htm#apex_System_system_resetPasswordWithEmailTemplate) in Salesforce Apex Developer Guide📕

This post contains few general exceptios which i have encountered. Comment down if you have encountered a different exception using this! 
