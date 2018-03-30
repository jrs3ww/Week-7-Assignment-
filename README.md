# Project 7 - WordPress Pentesting

Time Spent: 5 hours spent in total 

## Pentesting Report

1. Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: Unauthenticated attackers can inject JS into comments. The script is triggered when the comment is viewed. If triggered by an admin, the attacker can execute code on the server 
    - Vulnerability types: Cross-Site Scripting 
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: ![](https://github.com/jrs3ww/Week-7-Assignment-/blob/master/test1_comment.gif)
  - [ ] Steps to recreate: 
		1. Create a comment that has the desired script contained in it. 
		2. Then inside the '' of the script include at least 64KB of characters in the message.
			a. After a comment is long enough, not all of the contents of it is stored, which leads to just the script being posted. 
		3. Wait for admin to open comment. 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/4.2/src/wp-includes/comment.php)
2. Authenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: If an attacker has contributor or Contributor or Author level account, the attacker could insert HTML formatted text containing JS on a Page or Post.
    - Vulnerability types: Cross-Site Scripting 
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: ![](https://github.com/jrs3ww/Week-7-Assignment-/blob/master/test2_html.gif)
  - [ ] Steps to recreate: 
		1. Gain access to an Contributor or Author level account.
		2. Change the text type from "Visual" to "Text".
		3. Insert script.
		4. Submit Post or Page. 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/4.2/src/wp-includes/class-wp-editor.php)
3. Authenticated Cross-Site Scripting (XSS) via Media File Metadata
  - [ ] Summary: The metadata stored in MP3 files (ID3 Tags) are not properly sanitized if they are uploaded by an Editor or Administrator. So when an Editor or Admin posts the MP3 file inside of a playlist in a page or post, the script contained in the MP3 can run. 
    - Vulnerability types: Cross-Site Scripting 
    - Tested in version: 4.2
    - Fixed in version: 4.2.13
  - [ ] GIF Walkthrough: ![](https://github.com/jrs3ww/Week-7-Assignment-/blob/master/test3_mp3.gif)
  - [ ] Steps to recreate: 
		1. Create an MP3 file that has JS inside of its Metadata
		2. Get Admin or Editor to create a new Post or Page that has a playlist with the MP3 file contained in it. 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/4.2/src/wp-includes/pluggable.php)
	
## Assets 
https://www.securify.nl/advisory/SFY20160742/xss.mp3
 - Used to penetrate via Media File Metadata 

##Resources 

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- [Comment Vulnerability] http://klikki.fi/adv/wordpress2.html
- [HTML Text Vulnerability] https://klikki.fi/adv/wordpress3.html
- [Media File Metadata Vulnerability] https://sumofpwn.nl/advisory/2016/wordpress_audio_playlist_functionality_is_affected_by_cross_site_scripting.html


GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## License

    Copyright [2018] [Apache]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

