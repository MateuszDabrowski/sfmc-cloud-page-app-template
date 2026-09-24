# Salesforce Marketing Cloud Cloud Page App Templates

Read more about [SFMC Cloud Page Apps](https://mateuszdabrowski.pl/docs/usecase/sfmc-cloud-page-apps/).

Work in progress, more details soon :)

## Simple Cloud Page App

Whole App on a single Cloud Page

## Complex Cloud Page App

App split between Cloud Page (front end) and Code Resource (back end) for better UX.

## Security notes

- **The session id is the credential.** Anyone who knows a live session id can call the app as its owner. The templates mint the session id after the token exchange and never reuse the OAuth `state`, because whoever starts the sign-in knows `state` and could send the authorize link to a colleague who is already logged in to Marketing Cloud.
- **Protect the AuthLog Data Extension.** It holds session ids and access tokens, and any user with Data Extension access in the Business Unit can read it. Keep it in a folder only admins browse and set its retention to individual records after 1 day.
- **Content renders only after sign-in.** The protected part of the page sits inside an AMPscript `IF @appAuthenticated == 'true'` block, set by the SSJS gate. A failed sign-in, debugging left on, or a redirect that does not stop the page cannot render it.
- **Escape anything from the query string.** The error page and the debug output escape `error` and `error_description`, because a crafted link would otherwise run script on your Cloud Pages domain.
- **Switch `debugging` off in production.** Debug output is meant for building the app.

## Supporting Data Extensions

### AuthLog

| Name | DataType | Default Value | Length | Nullable |
|--|--|--|--|--|
| 🔑 session | Text | | 50 | No |
| appName | Text | | 100 | Yes |
| createdDate | Date | Current date | | Yes |
| token | Text | | 520 | Yes |
| tokenExpire | Date | | | Yes |
| userName | Text | | 100 | Yes |
| userEmail | Text | |  254 | Yes |

### ErrorLog

| Name | DataType | Default Value | Length | Nullable |
|--|--|--|--|--|
| 🔑 id | Text | | 36 | No |
| appName | Text | | 100 | Yes |
| errorMessage | Text | | 2000 | Yes |
| errorDescription | Text | | 2000 | Yes |
| errorDate | Date | Current date | | Yes |
