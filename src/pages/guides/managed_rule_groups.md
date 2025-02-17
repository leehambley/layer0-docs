---
title: Managed Rule Group Descriptions
---

## Layer0 Managed Rules {/*layer0-managed-rules*/}

<Callout type="danger">
	Layer0 recommends utilizing this rule group for all WAF use cases.
</Callout>

| Rule Name                           | Description                                                                                                                                                                                                                                                                                                                          | Log Name       |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------- |
| Cross-site scripting (XSS) Body     | Inspects the value of the request body and blocks common cross-site scripting (XSS) patterns using the built-in XSS detection rule in {{ PRODUCT_NAME }} WAF. Example patterns include scripts such as `<script>alert("hello")</script>`. CAUTION: This rule only inspects the first 8 KB of the request body.                       | `cssBody`      |
| Cross-site scripting (XSS) Cookie   | Inspects the value of cookie headers and blocks common cross-site scripting (XSS) patterns using the built-in XSS detection rule in {{ PRODUCT_NAME }} WAF. Example patterns include scripts such as `<script>alert("hello")</script>.`                                                                                              | `cssCookie`    |
| cssCookie                           | Cross-site scripting (XSS) Query. Inspects the value of query arguments and blocks common cross-site scripting (XSS) patterns using the built-in XSS detection rule in {{ PRODUCT_NAME }} WAF. Example patterns include scripts such as `<script>alert("hello")</script>`.                                                           | `cssArgs`      |
| Cross-site scripting (XSS) URI Path | Inspects the URI path and blocks requests that attempt to exploit RFI (Remote File Inclusion) in web applications by embedding URLs that contain IPv4 addresses. Examples include patterns such as `http://`, `https://`, `ftp://`, `ftps://`, and `file://`, with an IPv4 host header in the exploit attempt.                       | `cssPath`      |
| EC2 Body                            | Inspects for attempts to exfiltrate Amazon EC2 metadata from the request body. CAUTION: This rule only inspects the first 8 KB of the request body.                                                                                                                                                                                  | `metaBody`     |
| EC2 Cookie                          | Inspects for attempts to exfiltrate Amazon EC2 metadata from the request cookie.                                                                                                                                                                                                                                                     | `metaCookie`   |
| EC2 Query                           | Inspects for attempts to exfiltrate Amazon EC2 metadata from the request query arguments.                                                                                                                                                                                                                                            | `metaArgs`     |
| EC2 URI Path                        | Inspects for attempts to exfiltrate Amazon EC2 metadata from the request URI path.                                                                                                                                                                                                                                                   | `metaPath`     |
| General LFI Body                    | Inspects for the presence of Local File Inclusion (LFI) exploits in the request body. Examples include path traversal attempts using techniques such as ../../. CAUTION: This rule only inspects the first 8 KB of the request body                                                                                                  | `fileBody`     |
| General LFI Query                   | Inspects for the presence of Local File Inclusion (LFI) exploits in the query arguments. Examples include path traversal attempts using techniques such as ../../.                                                                                                                                                                   | `fileArgs`     |
| General LFI URI Path                | Inspects for the presence of Local File Inclusion (LFI) exploits in the URI path. Examples include path traversal attempts using techniques such as ../../.                                                                                                                                                                          | `filePath`     |
| General RFI BODY                    | Inspects for the presence of Local File Inclusion (LFI) exploits in the request body. Examples include path traversal attempts using techniques such as ../../. CAUTION: This rule only inspects the first 8 KB of the request body                                                                                                  | `remoteBody`   |
| General RFI Query                   | Inspects the values of all query parameters and blocks requests that attempt to exploit RFI (Remote File Inclusion) in web applications by embedding URLs that contain IPv4 addresses. Examples include patterns such as `http://`, `https://`, `ftp://`, `ftps://`, and `file://`, with an IPv4 host header in the exploit attempt. | `remoteArgs`   |
| General RFI URI Path                | Inspects the URI path and blocks requests that attempt to exploit RFI (Remote File Inclusion) in web applications by embedding URLs that contain IPv4 addresses. Examples include patterns such as `http://`, `https://`, `ftp://`, `ftps://`, and `file://,` with an IPv4 host header in the exploit attempt.                       | `remotePath`   |
| Invalid Argument                    | Inspects requests whose query arguments are system file extensions that the clients shouldn't read or run. Example patterns include extensions such as `.log` and `.ini.`                                                                                                                                                            | `invalidArgs`  |
| Invalid URI Path.                   | Inspects requests whose URI path includes system file extensions that the clients shouldn't read or run. Example patterns include extensions such as `.log` and `.ini`.                                                                                                                                                              | `invalidPath`  |
| Missing User Agent                  | Blocks requests with no HTTP User-Agent header.                                                                                                                                                                                                                                                                                      | `missingAgent` |
| Size - Body                         | Verifies that the request body size is at most 8 KB (8,192 bytes).                                                                                                                                                                                                                                                                   | `sizeBody`     |
| Size - Cookie                       | Verifies that the cookie header length is at most 10,240 bytes.                                                                                                                                                                                                                                                                      | `sizeCookie`   |
| Size - URI Path                     | Verifies that the URI path length is at most 1,024 bytes.                                                                                                                                                                                                                                                                            | `sizePath`     |
| Size - URI Query Size               | Verifies that the URI query string length is at most 2,048 bytes.                                                                                                                                                                                                                                                                    | `sizeArgs`     |

## Admin Page Protection Rule {/*admin-page-protection-rule*/}

| Rule Name          | Description                                                                                                                                          | Log Name        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| Protected URI Path | Inspects requests for URI paths that are generally reserved for administration of a webserver or application. Example patterns include `sqlmanager`. | `protectedPath` |

## Bad Input Rules {/*bad-input-rules*/}

<Callout type="danger">
	Layer0 recommends enabling the 'Bad Input - Log4J' rule on all WAF applications.
</Callout>

| Rule Name            | Description                                                                                                                                                                                                                                                             | Log Name      |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| Bad Input - Bad host | Inspects the host header in the request for patterns indicating localhost. Example patterns include localhost                                                                                                                                                           | `badHost`     |
| Bad Input - Bad path | Inspects the URI path for attempts to access exploitable web application paths. Example patterns include paths such as `web-inf`.                                                                                                                                       | `badPath`     |
| Bad Input - Log4js   | Inspects the request for the presence of the Log4j vulnerability CVE-2021-44228 and protects against Remote Code Execution (RCE) attempts. Example patterns include `${jndi:ldap://example.com/}`. CAUTION: This rule only inspects the first 8 KB of the request body. | 3             |
| Bad Input - Propfind | Inspects the HTTP method in the request for `PROPFIND`, which is a method similar to `HEAD`, but with the extra intention to exfiltrate XML objects.                                                                                                                    | `badProperty` |

## PHP Application Rules {/*php-application-rules*/}

| Rule Name   | Description                                                                                                                                                                      | Log Name  |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| PHP - Body  | Inspects the values of the request body for PHP script code injection attempts. Example patterns include functions such as `fsockopen` and the `$_GET` superglobal variable.     | `phpBody` |
| PHP - Query | Inspects the values of all query parameters for PHP script code injection attempts. Example patterns include functions such as `fsockopen` and the `$_GET` superglobal variable. | `phpArgs` |

## SQL Database Rules {/*sql-database-rules*/}

| Rule Name            | Description                                                                                                                                                                                                        | Log Name       |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------- |
| SQL - Body           | Uses the built-in {{ PRODUCT_NAME }} WAF SQL injection match statement to inspect the request body for patterns that match malicious SQL code. CAUTION: This rule only inspects the first 8 KB of the request body | `sqlBody`      |
| SQL - Cookie         | Uses the built-in {{ PRODUCT_NAME }} WAF SQL injection match statement to inspect the request cookie header for patterns that match malicious SQL code.                                                            | `sqlCookie`    |
| SQL - Query          | Uses the built-in {{ PRODUCT_NAME }} WAF SQL injection match statement to inspect the request query parameters for patterns that match malicious SQL code.                                                         | `sqlArgs`      |
| SQL - Query Extended | Inspects the values of all query parameters for patterns that match malicious SQL code. The patterns this rule inspects for aren't covered by the built-in {{ PRODUCT_NAME }} WAF SQL injection match statement.   | `sqlArgsExtra` |
| SQL - URI path       | Uses the built-in {{ PRODUCT_NAME }} WAF injection match statement to inspect the request URI path for patterns that match malicious SQL code.                                                                     | `sqlPath`      |

## Bot Control Rules {/*bot-control-rules*/}

| Rule Name           | Inspects for                                                                                                        | Log Name         |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------- |
| BOT - Advertising   | Bots that are used for advertising purposes.                                                                           | `botAds`         |
| BOT - Archiver      | Bots that are used for archiving purposes.                                                                             | `botArchiver`    |
| BOT - Browser       | Indications of an automated web browser.                                                                               | `botBrowser`     |
| BOT - Content       | Bots that are fetching content on behalf of an end user.                                                               | `botFetcher`     |
| BOT - Data center   | Data centers that are typically used by bots.                                                                          | `botProvider`    |
| BOT - HTTP Library  | HTTP libraries that are often used by bots.                                                                            | `botLib`         |
| BOT - Link checker  | Bots that check for broken links.                                                                                      | `botLinkChecker` |
| BOT - Miscellaneous | Miscellaneous bots.                                                                                                    | `botOther`       |
| BOT - Monitoring    | Bots that are used for monitoring purposes.                                                                            | `botPing`        |
| BOT - Scraping      | Web scraping frameworks.                                                                                               | `botScraper`     |
| BOT - Search Engine | Search engine bots. Verified search engines are not blocked.                                                           | `botSearch`      |
| BOT - Security      | Security-related bots.                                                                                                 | `botSecurity`    |
| BOT - SEO           | Bots that are used for search engine optimization.                                                                     | `botSeo`         |
| BOT - Social Media  | Bots that are used by social media platforms to provide content summaries. Verified social media bots are not blocked. | `botSocial`      |
| BOT - User agent    | User agent strings that don't seem to be from a web browser.                                                           | `botUserAgent`   |
