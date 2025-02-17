---
title: Security
---

## Overview {/*overview*/}

{{ PRODUCT_NAME }}’s platform is built to ensure your website and applications remain open for business by keeping you protected against a wide range of security risks without sacrificing performance.

A fully [PCI-compliant](#section_is_the_layer0_waf_a_pci_compliant_solution_) solution, {{ PRODUCT_NAME }} Security protects your business against a variety of common exploits like SQL injections, cross-site scripting (XSS), PHP injections, bot attacks, DDoS attacks, and other common vulnerabilities.

This guide shows you how to keep your site and platform secure using {{ PRODUCT_NAME }}.

## DDoS (Distributed Denial of Service) {/*ddos-distributed-denial-of-service*/}

{{ PRODUCT_NAME }} Enterprise customers enjoy always-on DDoS protection inside of our high-bandwidth, globally distributed network. Our solution offers basic protection against common layer 3 and 4 attacks in real-time so you never have to sacrifice performance for protection.

## WAF (Web Application Firewall) {/*waf-web-application-firewall*/}

### WAF Overview {/*waf-overview*/}

WAF is a web application firewall that helps protect your web applications and APIs against common web exploits an attacker may use to compromise your security, overwhelm resources, and affect the availability of your application.

Utilizing the {{ PRODUCT_NAME }} WAF allows you to monitor, filter, and block HTTP traffic against common vulnerabilities such as cross-site scripting (XSS) or SQL injection before they reach your origin.

The WAF includes Managed Rule Groups, managed by {{ PRODUCT_NAME }}, that can be configured in either a flagging or blocking mode. You can enable all of the rules within these groups or configure each independent rule within the group based on your needs.

### Managed Rule Groups {/*managed-rule-groups*/}

#### {{ PRODUCT_NAME }} Managed Rules {/*layer0-managed-rules*/}

​​The {{ PRODUCT_NAME }} Managed rule group contains rules that are generally applicable to web applications. This provides protection against exploitation of a wide range of vulnerabilities, including high risk and commonly occurring vulnerabilities described in OWASP&reg; publications such as [OWASP Top 10](https://owasp.org/www-project-top-ten/).

<Callout type="danger">
  Layer0 recommends utilizing this rule group for all WAF use cases.
</Callout>

[Layer0 Managed Rule Group Descriptions](managed_rule_groups#section_managed_rule_groups)

---

#### Admin Page Protection Rule {/*admin-page-protection-rule*/}

The Admin protection rule group contains rules that allow you to block external access to exposed administrative pages. This might be useful if you run third-party software or want to reduce the risk of a malicious actor gaining administrative access to your application.

[Admin Page Protection Rule Description](managed_rule_groups#section_admin_page_protection_rule)

---

#### Bad Input Rules {/*bad-input-rules*/}

The Bad Input rule group contains rules to block request patterns that are known to be invalid and are associated with exploitation or the discovery of Common Vulnerabilities and Exposures (CVEs). This can help reduce the risk of a known malicious actor discovering a vulnerable application.

<Callout type="danger">
  Layer0 recommends enabling the 'Bad Input - Log4J' rule on all WAF
  applications.
</Callout>

[Bad Input Rule Descriptions](managed_rule_groups#section_bad_input_rules)

---

#### PHP Application Rules {/*php-application-rules*/}

The PHP application rule group contains rules that block request patterns associated with the exploitation of vulnerabilities specific to the use of the PHP programming language. This includes the injection of unsafe PHP functions into requests.

[PHP Application Rule Descriptions](managed_rule_groups#section_php_application_rules)

---

#### SQL Database Rules {/*sql-database-rules*/}

The SQL database rule group contains rules to block request patterns associated with exploitation of SQL databases, like SQL injection attacks. This can help prevent remote injection of unauthorized queries. Evaluate this rule group for use if your application interfaces with an SQL database.

[SQL Database Rule Descriptions](managed_rule_groups#section_sql_database_rules)

---

#### Add Rule Groups to a WAF {/*add-rule-groups-to-a-waf*/}

![Add Rule Groups to WAF](/images/security/addrulegroup1.jpg?width=700 'Add Rule Groups to WAF')

1. Log in to the [Layer0 console](https://app.layer0.co/).
1. Click _SECURITY_ from the top banner to launch the WAF Security Rules page.
1. Select [_WAF-1_ or _WAF-2_](#section_what_s_the_difference_between_waf_1_and_waf_2_) from the first dropdown and the [configuration version](#section_how_do_i_know_which_version_to_use_) from the second.
1. Click _EDIT_ to set your security rules.

![Add Rule Groups to WAF2](/images/security/addrulegroup2.jpg?width=700 'Add Rule Groups to WAF2')

5. Select the _Set all rules to …_ dropdown. Hover over the dropdown for the rule group's description.
6. Choose the action for the group: _Off_, [_Flag_, or _Block_](#section_what_is_the_difference_between_flagging_and_blocking_a_rule_or_rule_group_).
7. When you’ve made all your changes, click _ACTIVATE_. You will see a popup confirming your rule changes.
8. Click _ACTIVATE_ to confirm the rule changes or _CANCEL_ to continue editing. When your changes have deployed, the version will update with the next incremental number.

---

#### Add Single Rules to a WAF {/*add-single-rules-to-a-waf*/}

![Add Single Rule to WAF](/images/security/addrulegroup1.jpg?width=700 'Add Single Rule to WAF')

1. Log in to the [Layer0 console](https://app.layer0.co/).
1. Click _SECURITY_ from the top banner to launch the WAF Security Rules page.
1. Select [_WAF-1_ or _WAF-2_](#section_what_s_the_difference_between_waf_1_and_waf_2_) from the first dropdown and the [configuration version](#section_how_do_i_know_which_version_to_use_) from the second.
1. Click _EDIT_ to set your security rules.

![Add Single Rule to WAF2](/images/security/addsinglerule.jpg?width=700 'Add Single Rule to WAF')

5. If collapsed, expand the Rule Group dropdown using the arrow to its left. You can hover over the rule name or the Flag/Block dropdown to view the rule's description.
6. Click the _Flag/Block_ dropdown.
7. Select the action for the rules you want to change: _Off_, [_Flag_, or _Block_](#section_what_is_the_difference_between_flagging_and_blocking_a_rule_or_rule_group_).
8. When you’ve made all your changes, click _ACTIVATE_. You will see a popup confirming your rule changes.
9. Click _ACTIVATE_ to confirm the rule changes or _CANCEL_ to continue editing. When your changes have deployed, the version will update with the next incremental number.

---

#### Apply a WAF to Your Environment {/*apply-a-waf-to-your-environment*/}

Prerequisite: Configured WAF rules and/or rule groups.

Once you’ve configured the WAF rules you want to use, you need to apply them to the corresponding environments you want to deploy them on. Rules are NOT applied to traffic until you take this step to apply them.

Follow these steps to add a WAF to an environment:

![Apply WAF to Environment](/images/security/addrg3.jpg?width=700 'Apply WAF to Environment')

1. Log in to the [Layer0 console](https://app.layer0.co/) and select your site.
1. Click the ENVIRONMENTS tab.
1. Choose an environment from the list.

![Security Configuration](/images/security/security.jpg?width=700 'Security Configuration')

4. Select _CONFIGURATION_ from the top navigation.
1. Click _EDIT_.
1. Scroll down to the Security section.
1. From the dropdown, select an active WAF to add.
1. Click the ACTIVATE button from either the top or the bottom of the page.

## Bot Detection {/*bot-detection*/}

### Detect Bots with Managed Rules {/*detect-bots-with-managed-rules*/}

The {{ PRODUCT_NAME }} Bot protection contains rules to block and manage requests from bots. You are charged additional fees when you use this product.

The Bot Control product applies labels to a set of verifiable bots that are commonly allowed. The rule group doesn't block this category of commonly allowed bots.

**Bot Control Rule Group**: In addition to the WAF rule groups, {{ PRODUCT_NAME }} offers an additional Managed Rule Group for bots that allows you to take action against common bots that may impact the performance and availability of your web application or APIs.

You can monitor the impact of your bots by flagging each bot type of request gaining insights into SEO bots, scraping bots, advertising bots, malicious user agent bots, and several other categories of bots.

[Bot Control Rule Descriptions](managed_rule_groups#section_bot_rules)

### Detect Bots with EdgeJS {/*detect-bots-with-edgejs*/}

#### General Information {/*general-information*/}

{{ PRODUCT_NAME }} examines the `user-agent` header in an incoming request to determine if it includes a string that indicates if it is a bot, and if so, injects `1` in the `x-0-device-is-bot` request header, which will be visible to your server code. If the `user-agent` header does not include any of the strings indicating a bot, a `0` value is injected.

#### User Agents and Bots {/*user-agents-and-bots*/}

The following table list the user agents that {{ PRODUCT_NAME }} examines and describes the corresponding bots.

| User Agent              | Bot Description                                                                                                                                                                                                                                 |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| embedly                 | Embed.ly web crawler bot that performs HTTP requests most often in automatic mode.                                                                                                                                                              |
| facebookexternalhit     | Facebook bot that crawls the HTML of social plugins, apps, and websites shared on Facebook. The bot gathers and caches data (title, description, thumbnail image) about the shared content and presents the data as a preview.                  |
| flipboard               | Flipboard Proxy Service bot that runs in response to a user request for the service to scan a social media feed such as Twitter, and construct a processed feed of items to deliver in real time.                                               |
| googlepagesspeed        | Google bot that assists in ranking search results based on page load speed.                                                                                                                                                                     |
| Google web/snippet      | Google+ Enterprise bot that extracts high-level data from a URL posted on Google+ Enterprise and presents the data as a snippet of the URL.                                                                                                     |
| headless                | Bots, usually scripts, that run on a scheduled basis or are triggered from an external system. Headless bots usually perform activities like sending alerts or daily digest messages. The scripts usually run for a short time, then terminate. |
| ia_archiver             | Amazon Alexa bot that crawls web sites for issues related to Amazon's Site Audit service.                                                                                                                                                       |
| outbrain                | Outbrain Recommendation Platform chat bot.                                                                                                                                                                                                      |
| pinterest               | Automated Pinterest bot that creates boards and schedules pins to post to customer accounts.                                                                                                                                                    |
| prerender               | Prerender.io hosted service bot that produces an easily crawled version of dynamically rendered pages, allowing indexing by search engines.                                                                                                     |
| preview                 | Yahoo bot that extracts data (title, description, thumbnail images) from a URL embedded in an email and presents the data as a preview of the URL                                                                                               |
| qwantify                | Web crawler bot that indexes content for the Qwant search engine.                                                                                                                                                                               |
| scanner                 | Bots that analyze how well your website and its security measures respond to various bot threats.                                                                                                                                               |
| slurp                   | Yahoo Search bot for crawling and indexing web page information.                                                                                                                                                                                |
| spider                  | General purpose automated bots that crawl the web to index web page information.                                                                                                                                                                |
| tumblr                  | Tumblr bot that performs automated HTTP requests as a web crawler.                                                                                                                                                                              |
| vkshare                 | VK social network bot that performs automated HTTP requests usually as a web crawler.                                                                                                                                                           |
| w3c_validator           | W3C bot that checks Web documents in formats like HTML and XHTML for conformance to W3C Recommendations and other standards.                                                                                                                    |
| whatsapp                | Whatsapp platform chat bot.                                                                                                                                                                                                                     |
| xing-contenttabreceiver | Xing social network crawler bot that indexes content for the Xing social network.                                                                                                                                                               |
| yahoo                   | Another Yahoo Search robot for crawling and indexing web page information.                                                                                                                                                                      |

If the set of bots detected by {{ PRODUCT_NAME }} is not sufficient for your needs, you can easily add your own bot detection through [EdgeJS](/guides/routing) and its [`match`](/docs/api/core/classes/_router_router_.router.html#match) and [`setRequestHeader`](/docs/api/core/classes/_router_responsewriter_.responsewriter.html#setrequestheader) APIs:

```js
router.match(
  {
    headers: {
      'user-agent': /^regex-for-your-bot-detection$/i,
    },
  },
  ({ setRequestHeader }) => {
    setRequestHeader('my-bot-detection-is-bot', '1')
  },
)
// ... all your other routes go here and they can match on `my-bot-detection-is-bot: 1`
```

The above code will match all the routes that even have a `user-agent` header and then inject the `my-bot-detection-is-bot` when the value of the user agent header matches the given regex. Once the header has been injected, the later routes can test for it and implement bot handling. Or, you could just let the header be sent upstream for your backend to handle it.

## Security Reporting {/*security-reporting*/}

![Reporting](/images/security/addrg3.jpg?width=700 'Reporting')

1. Log in to the [Layer0 console](https://app.layer0.co/) and select your site.
1. Click the ENVIRONMENTS tab.
1. Choose an environment.
1. Click the SECURITY tab from the top page navigation.

### Security Activity {/*security-activity*/}

![WAF Activity](/images/security/wafactivity.jpg?width=700 'WAF Activity')

|     | View Option                                             | Access                                   |
| --- | ------------------------------------------------------- | ---------------------------------------- |
| a.  | Deployment number                                       | Toggle on/off via WAF Activity settings. |
| b.  | Number of requests by action (passed, flagged, blocked) | Hover over graph data.                   |
| c.  | Requests by action (passed, flagged, blocked)           | Toggle the checkboxes.                   |
| d.  | Deployments and/or full cache flushes                   | Toggle on/off via WAF Activity settings. |

### Rules Applied {/*rules-applied*/}

![Rules Applied](/images/security/rulesapplied.png?width=700 'Rules Applied')

|     | View Option                     | Access                                                                                                                                                                                          |
| --- | ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| a.  | Date range                      | Select 24 hour, 7 days, or 28 days.                                                                                                                                                             |
| b.  | Flagged and/or Blocked requests | Toggle the Flagged and Blocked buttons.                                                                                                                                                         |
| c.  | Graph of rules applied          | Click inside the graph to list the names of the rules that have been applied to your Bot Control or {{ PRODUCT_NAME }} Managed rules. Click _Back to Rule Sets_ to return to the previous view. |

### Rules Section {/*rules-section*/}

![Rules](/images/security/rules.jpg?width=700 'Rules')

|     | View Option   | Access                                                                                                                                         |
| --- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| a.  | Rules by type | Expand or collapse the list using the arrow to the left of the rule type.                                                                      |
| b.  | Route details | Click the rule name to view route information for that rule, including its path and number/percentage of total, flagged, and blocked requests. |

### Logs {/*logs*/}

Here is a sample log file highlighting the WAF data ("waf":"botLib,flagged","wafv":"WAF-1,2"): the action applied, the mode, the WAF name, and the version number, respectively.

![WAF Log File Example](/images/security/log.jpg?width=700 'WAF Log File Example')

## Website Security with EdgeJS {/*website-security-with-edgejs*/}

### Content Security Policy (CSP) {/*content-security-policy-csp*/}

[Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement to distribution of malware.

You can easily add CSP headers to your site via a catch-all route near the top of your router.

To enforce a content security policy:

```js
new Router().match('/:path*', ({ setResponseHeader }) => {
  setResponseHeader(
    'Content-Security-Policy',
    "default-src 'self'; report-uri http://reportcollector.example.com/collector.cgi",
  )
})
// The rest of your router...
```

To enable a content security policy in report-only mode:

```js
new Router().match('/:path*', ({ setResponseHeader }) => {
  setResponseHeader('Content-Security-Policy-Report-Only', "default-src 'self'")
})
// The rest of your router...
```

### Enabling Basic Authentication {/*enabling-basic-authentication*/}

You can add basic authentication to your site using the `requireBasicAuth` router method. For example, add the following to the top of your router:

```js
router.requireBasicAuth({
  username: process.env.BASIC_AUTH_USERNAME,
  password: process.env.BASIC_AUTH_PASSWORD,
})
```

Then, add `BASIC_AUTH_USERNAME` and `BASIC_AUTH_PASSWORD` environment variables to each environment that should enforce
basic authentication. Any environment without those environment variables will not enforce basic authentication.

Once deployed, the router will return 403 Forbidden for requests that have the incorrect basic authentication token, and 401 Unauthorized for requests that have no basic authentication token.

### SSL {/*ssl*/}

By default {{ PRODUCT_NAME }} only serves traffic over the `https` protocol. It automatically redirects `http` requests to the same URL, including any query strings, on `https`.

We strongly discourage the use of `http` protocol, but if you _must_ enable it, then you can do so by adding `protocol: 'http'` to your route criteria. For example:

```js
// routes.js

// Respond to Let's Encrypt HTTP-01 challenge.
router.match(
  {
    protocol: 'http',
    path: '/.well-known/acme-challenge/<your token>',
  },
  ({ send }) => {
    send('<token value>')
  },
)
```

If you want the route to match both `http` and `https` protocols you can match on `protocol: /^https?$/`. If no route is matched on `http` protocol then {{ PRODUCT_NAME }} will fallback on its default behavior of automatically redirecting the request to `https`.

Additionally:

- A request's protocol can be determined by reading the [`{{ HEADER_PREFIX }}-protocol`](request_headers#section_general_headers) request header or the [`request.secure`](/docs/api/core/interfaces/_router_request_.request.html#secure) property.
- During local development all requests will appear secure by default. To test your router for `http` protocol matching you must either set the `local_{{ COOKIE_PREFIX }}_emulate_http_protocol` cookie to `true` (if using a browser) or send an `{{ HEADER_PREFIX }}-protocol` request header set to `http`.

### Secrets {/*secrets*/}

Rather than putting secret values such as API keys in your code and checking them into source control, you can securely
store them in environment variables, then access them in your code from `process.env`. To configure environment variables,
navigate to your environment, click _EDIT_, then under Environment Variables, click _ADD VARIABLE_.

![networking](/images/security/environment-variables.png?width=700)

As of {{ PRODUCT_NAME }} CLI version 2.19.0, when you deploy to an environment using a deploy token, for example by running `{{ CLI_NAME }} deploy my-team --environment=production --token=(my token)` option, all environment variables are pulled down from the {{ PRODUCT_NAME }} Developer Console and applied to `process.env` so they can be accessed at build time. This allows you to store all of your build and runtime secrets in a single place, {{ PRODUCT_NAME }} Developer Console, rather than storing some in your CI system's secret manager.

### Cache Poisoning {/*cache-poisoning*/}

[Cache poisoning attack](https://owasp.org/www-community/attacks/Cache_Poisoning) is described by OWASP&reg; as:

> The impact of a maliciously constructed response can be magnified if it is cached either by a web cache used by multiple users or even the browser cache of a single user. If a response is cached in a shared web cache, such as those commonly found in proxy servers, then all users of that cache will continue to receive the malicious content until the cache entry is purged.

To guard against this attack you must ensure that all the request parameters that influence the rendering of the content are part of your [custom cache key](caching#section_customizing_the_cache_key). {{ PRODUCT_NAME }} will [automatically include](caching#section_cache_key) the `host` header and URL. Including other request headers and cookies are your responsibility.

For example, if you are rendering content based on a custom language cookie, then you must include it in your custom cache key:

```js
import { CustomCacheKey } from '{{ PACKAGE_NAME }}/core/router'

router.get('/some/path/depending/on/language/cookie', ({ cache }) => {
  cache({
    key: new CustomCacheKey().addCookie('language'),
    // Other options...
  })
})
```

## FAQs {/*faqs*/}

### What’s the difference between WAF-1 and WAF-2? {/*whats-the-difference-between-waf-1-and-waf-2*/}

You can configure 2 different WAF instances, allowing you to apply different sets of security rules to different environments.

### How do I know which version to use? {/*how-do-i-know-which-version-to-use*/}

Like all {{ PRODUCT_NAME }} products, WAF gives you access to all previous and active versions of your configuration so you have historical setups in case you need to roll back the current version.While editing, the version is in a _Draft_ state; once activated, the version is _Active_.

### What is the difference between flagging and blocking a rule or rule group? {/*what-is-the-difference-between-flagging-and-blocking-a-rule-or-rule-group*/}

To flag a rule or rule group means to mark it if the rule would have been activated without actually denying the traffic. In contrast, when you block a rule or rule group, traffic is denied on affected routes. You can view both flagged and blocked data in your [Layer0 console](https://app.layer0.co/).

### What are {{ PRODUCT_NAME }} Managed Rules and why should I apply this rule group? {/*what-are-layer0-managed-rules-and-why-should-i-apply-this-rule-group*/}

Managed rules block specific known threats. Layer0 recommends this rule group for all WAF use cases.

Note: Layer0 recommends that all customers activate the _Bad Input - Log4J_ rule group.

### Is the Layer0 WAF a PCI-compliant solution? {/*is-the-layer0-waf-a-pci-compliant-solution*/}

Yes. Layer0 maintains PCI-DSS Level 1 compliance by undergoing annual audits from approved Visa and MasterCard auditors.

### What is the minimum level of encryption for {{ PRODUCT_NAME }}? {/*what-is-the-minimum-level-of-encryption-for-layer0*/}

{{ PRODUCT_NAME }} enforces a minimum version of TLS 1.2 or higher.
