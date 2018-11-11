# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **three vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: If the comment text is long enough, it will be truncated when inserted in the database. The MySQL TEXT type size limit is 64 kilobytes, so the comment has to be long. 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: <img src="https://github.com/edwin0108/WebSecurity_week7/blob/master/XSS64kb.gif" width="700">
  - [ ] Steps to recreate: comment a post with >64kb plus the following command:
			<a title='x onmouseover=alert(unescape(/hello%20world/.source)) 	style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>
2. Authenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: Under default configuration, the attack requires a Contributor or Author level account. The attacker would insert specially formatted HTML containing JavaScript on a WordPress page or post. Some special configurations may allow posting or editing page content for unauthenticated users. 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: <img src="https://github.com/edwin0108/WebSecurity_week7/blob/master/xssmedia.gif" width="700">
  - [ ] Steps to recreate: insert a script command and package it as a mp3 file and upload it to wordpress, refresh the page after upload and the script should be triggered.
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
1. (Required) Vulnerability Name or ID
  - [ ] Summary: An attacker can inject a malicious script in to the filename which a victim tries to upload leading to XSS inside the administrators control panel. Two different "file to large" cases end up in interpolating the file name and appending it into DOM unsanitized leading to XSS.
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.15
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: Create a 20MB file called "Dinosaurs secret life<img src=x onerror=alert(1)>.png", and upload to the media manager, refresh the page after upload and the script should be triggered.
  - [ ] Affected source code: 
    - [Link 1](https://github.com/WordPress/WordPress/commit/28f838ca3ee205b6f39cd2bf23eb4e5f52796bd7)


## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)


## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2018] [Ka Shing Wai]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
