# Update Blog Using Git

Writing a blog has certainly advanced a lot over the years. My first experience in dealing with a blog was way back when [Geocities](https://en.wikipedia.org/wiki/Yahoo!_GeoCities) was still a thing. The process of updating a Geocities website required knowing enough HTML to know where to update your thoughts and enough CSS to make what you wanted to say readable. While I'm sure there were helpful tools, I typically updated everything in a .txt document using Notepad and then copied and pasted that information into the field box, before mashing F5 to check if my new update broke everything. If my changes did break it, I would then undo back to the previous version and try again; or if my undo didn't work, open one of the many previous versions I had saved on my computer desktop.  

Luckily, there are many more options - source control and hosting - available to us now. As mentioned in my first post, this website is hosted on GitHub using a Jekyll template with my posts being done in markdown. While it's certainly more technically complex than the old HTML document (although still a valid option), using Git as source control and using Markdown as markup makes things far easier. Instead of hacking together HTML and finding out if it all works at the end, I can view the markdown in my editor ([Atom](https://github.com/atom)) and use Git to update the hosting. All of this is extremely easy to set up and you can have it running in no time.

If you follow my first post, you'll have a folder in GitHub with the name of your website's URL. If you're using Linux and have Git installed, pulling your website or repository down is as easy as using Git Clone on it -- using your information instead of mine.  
```
git init
git clone https://github.com/davidemily/davidemily.github.io.git
atom davidemily.github.io
```
These commands will use Git to clone the repository stored on GitHub and use GitHub's Atom edit to open the folder. After creating the post, you can use the same terminal window to commit and push your changes back up to the repository on GitHub. Doing it this way will help you leverage the usefulness of the Atom editor and the source control Git provides. It also means that your files on your local machine and on GitHub will stay up-to-date with each other.  
```
git add davidemily.github.io/
git commit -m "adding new post to my website!"
git push master
```  
It's amazing to see the advancement in technology from the days of Geocities to what we have know for web hosting. While the idea of it is the same, the tools we have now give us a much quicker feedback and take away many of the headaches that I had has a kid, keeping my website up to date and looking presentable.
