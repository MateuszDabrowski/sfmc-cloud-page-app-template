# Salesforce Marketing Cloud Cloud Page App Templates

## Simple Cloud Page App

Whole App on a single Cloud Page

## Complex Cloud Page App

App split between Cloud Page (front end) and Code Resource (back end) for better UX.

## Supporting Data Extensions

### AuthLog

| Name | DataType | Default Value | Length | Nullable |
|--|--|--|--|--|
| 🔑 session | Text | | 50 | No |
| appName | Text | | 100 | Yes |
| createdDate | Date | Current date | | Yes |
| token | Text | | 520 | Yes |
| tokenExpire | Date | | | Yes |
| userName | Text | 100 | | Yes |
| userEmail | Text | 254 | | Yes |

### ErrorLog

| Name | DataType | Default Value | Length | Nullable |
|--|--|--|--|--|
| 🔑 id | Text | | 36 | No |
| appName | Text | | 100 | Yes |
| errorMessage | Text | 2000 | | Yes |
| errorDescription | Text | 2000 | | Yes |
| errorDate | Date | Current date | | Yes |

Read more about [SFMC Cloud Page Apps](https://mateuszdabrowski.pl/docs/usecase/sfmc-cloud-page-apps/).
