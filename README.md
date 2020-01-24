# static-site-lock
A simple mechanism for adding straightforward password protection to static websites.

The idea for Static Site Lock was initially developed when I was looking for a simple serverless solution to protect a client's website project while it was being developed in the staging environment, meaning that the client could view the website remotely without letting the "regular Joe" see the unfinished project. I stumbled upon Matteo Brusa's [Password-protection-for-static-pages](https://github.com/matteobrusa/Password-protection-for-static-pages) GitHub project, it was a simple and straightforward solution but it lacked any polish on the front-end so I decided to rectify that and build upon the previous implementation to add my own spin to it.

While I found a more appropriate password protection method for my project through the use of cPanel's "Directory Privacy" settings, I still think that this project would be useful to individuals looking for password protection for small project.

*If you'd like to test drive Static Site Lock you can take a look at the [Static Site Lock](https://ronan-smith.github.io/static-site-lock/) demo environment, using `Password123` as the demo password.*
## Setup
The setup/deployment of Static Site Lock is fairly straightforward:
1. **Host** - Upload the `index.html` file at the root of this repository to your static hosting package.
2. **Set Password** - Navigate to the page in your browser and input your preferred password in the password field. The page will signal that the password is incorrect but this is normal. Copy the string of letters and numbers that has been generated after the `#` symbol in the current URL of the page.
3. **Create Directory** - Create a folder in the same directory as the previously placed `index.html` file named with the string copied from the URL.
4. **Upload** - Upload the files of your static website to the folder created in step three, including the `index.html` file of your website.

The structure of the final file system should be:
```
- index.html (file placed in step one)
- hash (folder named with the string copied from the URL)
    - index.html (index file of your static website)
    ... the rest of your static website files.
```
## Considerations
While Static Site Lock should be pretty secure, there are some things that you will need to take into consideration:
* **HTTPS** - Ensure that your website runs **forced** HTTPS as the password hash is transmitted in the URL.
* **Directory Listing** - Make sure you disable "directory listing" on your selected hosting service, else a visitor will be able to bypass the password protection.
* **Brute Force** - At the moment there is no protection against brute force attacks, so pick a really strong password.
* **Site Structure** - Remember to think about the resource links within your static website, links relative to the root of the site will of course now point to the directory with Static Site Lock within it.
* **Indexing** - Remember that there is a chance that a search engine may index your password protected pages in search results.

## Credits
Special thanks to Matteo Brusa, I have based Static Site Lock on the initial implementation of Matteo Brusa's [Password-protection-for-static-pages](https://github.com/matteobrusa/Password-protection-for-static-pages/blob/master/README.md) project.
