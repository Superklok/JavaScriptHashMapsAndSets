# JavaScript Subdomain Visit Count

## Challenge:

A website domain `"discuss.superklok.com"` consists of various subdomains. At the top level, we have `"com"`, at the next level, we have `"superklok.com"` and at the lowest level, `"discuss.superklok.com"`. When we visit a domain like `"discuss.superklok.com"`, we will also visit the parent domains `"superklok.com"` and `"com"` implicitly.

A count-paired domain is a domain that has one of the two formats `"rep d1.d2.d3"` or `"rep d1.d2"` where `rep` is the number of visits to the domain and `d1.d2.d3` is the domain itself.

For example, `"9001 discuss.superklok.com"` is a count-paired domain that indicates that `discuss.superklok.com` was visited `9001` times.

Given an array of count-paired domains `cpdomains`, return an array of the count-paired domains of each subdomain in the input. You may return the answer in any order.

### 1<sup>st</sup> Example:

`Input: cpdomains = ["9001 discuss.superklok.com"]`
<br/>
`Output: ["9001 superklok.com","9001 discuss.superklok.com","9001 com"]`
<br/>
`Explanation: We only have one website domain: "discuss.superklok.com".`
<br/>
`As discussed above, the subdomain "superklok.com" and "com" will also be visited.`
<br/>
`So they will all be visited 9001 times.`

### 2<sup>nd</sup> Example:

`Input: cpdomains = ["900 trevmorin.mail.com", "50 jetwheelreel.com", "1 currentcourant.mail.com", "5 swingcars.net"]`
<br/>
`Output: ["901 mail.com","50 jetwheelreel.com","900 trevmorin.mail.com","5 swingcars.net","5 org","1 currentcourant.mail.com","951 com"]`
<br/>
`Explanation: We will visit "trevmorin.mail.com" 900 times, "jetwheelreel.com" 50 times, "currentcourant.mail.com" once and "swingcars.net" 5 times.`
<br/>
`For the subdomains, we will visit "mail.com" 900 + 1 = 901 times, "com" 900 + 50 + 1 = 951 times, and "org" 5 times.`

### Constraints:

`1 <= cpdomain.length <= 100`
<br/>
`1 <= cpdomain[i].length <= 100`
<br/>
`cpdomain[i]` follows either the `"repᵢ d1ᵢ.d2ᵢ.d3ᵢ"` format or the `"repᵢ d1ᵢ.d2ᵢ"` format.
<br/>
`repᵢ` is an integer in the range `[1, 10⁴]`.
<br/>
`d1ᵢ`, `d2ᵢ`, and `d3ᵢ` consist of lowercase English letters.

## Solution:

`const subdomainVisits = (cpdomains) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let visitCounts = {};`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`for (let i = 0; i < cpdomains.length; i++) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const [visits, domains] = cpdomains[i].split(' ');`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let subdomains = domains.split('.');`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`while(subdomains.length) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let subdomain = subdomains.join('.');`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`visitCounts[subdomain] = visitCounts.hasOwnProperty(subdomain) ?`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Number(visitCounts[subdomain]) + Number(visits) :`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`visits;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`subdomains.shift();`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return Object.keys(visitCounts).map((key) => \`${visitCounts[key]} ${key}\`);
<br/>
`};`
<br/>
<br/>