# Project 7 - WordPress Pentesting

Time spent: **8** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) WordPress  4.0-4.7.2 - Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
  - [X] Summary: "XSS attack using YouTube URL Embeds" ([CVE Reference Link](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6817))
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.13
  - [X] GIF Walkthrough: ![](https://i.imgur.com/lKyH5SQ.gif)
  - [X] Steps to recreate:
	- From the WordPress admin panel, create a new post
	- Within the post, insert the following malicious youtube embed url,
	
	`[embed src='https://youtube.com/embed/12345\x3csvg onload=alert(1)\x3e'][/embed]`	
	
	- Next publish this post
	- After publishing, when the post is viewed the alert is triggered
	- Reference used: [Link 1](https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html)
  - [X] Affected source code:
    - [Link 2](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)
	
2. (Required) WordPress <= 4.3 - Authenticated Shortcode Tags Cross-Site Scripting (XSS)
  - [X] Summary: "XSS attack using mishandling of unclosed HTML elements during processing of shortcode tags" ([CVE Reference Link](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5714))
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.5
  - [X] GIF Walkthrough: ![](https://i.imgur.com/dUa6mac.gif)
  - [X] Steps to recreate:
	- From the WordPress admin panel, create a new post
	- Within the post, insert the following payload,
	
	`TEST!!![caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">Click me</a>`
	
	- Next publish and view the post
	- While viewing the post, whenever the mouse hovers over "Click me", the alert is triggered
	- Reference used: [Link 3](https://wpvulndb.com/vulnerabilities/8186)
  - [X] Affected source code:
    - [Link 4](https://github.com/WordPress/WordPress/commit/f72b21af23da6b6d54208e5c1d65ececdaa109c8)
	
3. (Required) WordPress <= 4.2.2 - Authenticated Stored Cross-Site Scripting (XSS)
  - [X] Summary: "XSS attack using carefully crafted shortcode inside an HTML element" ([CVE Reference Link](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5622))
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [X] GIF Walkthrough: ![](https://i.imgur.com/ZBb1hvq.gif) 
  - [X] Steps to recreate:
	- From the WordPress admin panel, create a new post
	- Within the post, insert the following code,
	
	`<a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>`
	
	- Next publish and view the post
	- While viewing the post, whenever the mouse hovers over "link", the alert is triggered
	- Reference used: [Link 5](https://wpvulndb.com/vulnerabilities/8111)  
  - [X] Affected source code:
    - [Link 6](https://core.trac.wordpress.org/changeset/33359)

	
4. (Optional) WordPress  3.7-4.4 - Authenticated Cross-Site Scripting (XSS)
  - [X] Summary: "XSS attack using theme name" ([CVE Reference Link](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-1564))
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.6
  - [X] GIF Walkthrough: ![](https://i.imgur.com/YEKGgEe.gif)
  - [X] Steps to recreate:
	- From the WordPress admin panel, create a new post
	- Within the post, enter a web address with `?theme=<svg onload=alert(1)>` at the end. For example,
		`http://www.example.com?theme=<svg onload=alert(1)>`
	- Next publish this post
	- After publishing, when the post is viewed the alert is triggered
  	- Reference used: [Link 7](https://wpvulndb.com/vulnerabilities/8358)
  - [X] Affected source code:
    - [Link 8](https://github.com/WordPress/WordPress/commit/7ab65139c6838910426567849c7abed723932b87) 

5. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 9](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)	
	
## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

	None

## License

    Copyright [2018] [Kevin Shah]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.