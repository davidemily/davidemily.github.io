# Clean Code Chap 2  
Ahh chapter 2 of Clean Code. For those just joining, I wanted to finally finish reading [Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882) and saw typing up my thoughts as a way to stay motivated. If you're interested in following my thoughts, chapter 1 was posted [here](https://davidemily.github.io/2019/clean-code-chapter-1/).  

Chapter 2's title is "Meaningful Names", which sufficiently hints at what the chapter is about. One thing I found particularly interesting about this chapter is that much of the material seems pretty common knowledge but also something that we should focus more on. As Robert Martin states, 
> "Names are everywhere in software. We name our variables, our functions, our arguments, classes and packages. We name our source files and directories that contain thm. We name our jar files and war files and ear files. We name and name and name."  

I love this saying. It perfectly annotates what programmers do, name things. I've heard many people refer to programming more as art and less of a science and I think that's very true. Maybe some classes over English and wording would have been more helpful than the ton of math classes I had to take... maybe. Anywho, let's get on to learning how we can be better namers and, in turn, better programmers. The chapter covers many different thoughts and I hope all of you eventually read it. I wanted to cover some of the main points in hope that I remember to use them on the job.  

#### Use Intention-Revealing Names  
Of all the naming rules covered, I find this one the most important. I remember very distinctly the use of "records" or "recordsList" variable names on the job. While at the time it made perfect sense, only to return several months later and be unable to recall what type of records it was. Furthermore, how did a list of "records" differentiate from "recordsList"? The book goes even further into detail to abstract out comparisons to a useful naming standard, which I think is a great help. Sure comparing the count of "recordsList" against 5 meant perfect sense at the time but it would have been much easier to understand with a comparison against "full application record".  

#### Avoid Disinformation  
I found this section pretty interesting but perhaps not as impact on my day-to-day job. Perhaps it is just the environment I work in - all Microsoft tech, very intelligent people, particular pieces of the product - but I find a general lack of disinformation in our code. I think this is one of the advantages of large corporations and teams with specific goals, my team's jargon matches several of the team's I work with. I can see this becoming more of a problem in environments with different operating systems, third party software, and tools. I think a lot of this ties in with being mindful that other environments and tools exist.  

I do remember a time when our team would pass around the term "cron". Coming from a Linux environment, I was confused on where our cron job was being ran and how to modify it, only to find out that it was instead a house-spun, scheduled program that runs on a timer. While this only caused a thirty second delay while someone explained it to me, if this software was passed off to another team it could be have been more harmful.  

#### Use Pronounceable Names  
While I get a chuckle out of the mental image of me asking my coworker how function "Xyz23gh" works, I am glad I don't deal with that. This is one of the sections that I think is pretty common sense and actually kind of difficult to do. Maybe it is just my experience working with bright individuals but I can't imagine writing a function and not naming it something easy to pronounce. With naming it something pronounceable, comes the advantage of being able to call out a specific part of the code and have someone know exactly where it is, or where to find it. If there's a problem in "GetRecordsAsync", I'll probably be able to find it more quickly than trying to spell "RecPulAsy".  

#### Class Names and Method Names  
> "A class name should be a verb. A method name should be a noun."  

Something that makes total sense when read but can be difficult to remember while you're coding. It can be a lot harder than typically thought to keep them separate, not because we're not all smart people but just due to how language works. If I was making some kind of blogging software, the variable name "reader" might make perfect sense to me as class name for someone who is consuming my blog. "Reader" might also make perfect sense as method name to reflect me consuming an API. Instead of making this mistake, a better option (although I'm sure even better ones exist) might be to call the class "Customer" or "Account" and the method "SaveArticlesApi" or "AddEmployee".  

Additionally, it's important to stick to a naming standard and not to be too creative. If your entire codebase is using the action term "Retrieve" it makes sense to continue that pattern and not to start randomly starting the method with "Pull". It also makes sense to not name classes or methods after inside jokes on the team. While I'll probably chuckle if I read a method named after an event that happened on my team months ago; I would probably not chuckle if I read about an event that happened on another team, I would probably just be confused and need clarification.  

#### Conclusion  
While this is not an exhausted list of all the naming standards, these are the ones I found most useful. I wanted to leave the other tips out so I don't steal Robert Martin's thunder and I suggest reading over this chapter if only to expand on the tips I mentioned. This chapter really hit me not because it gave me ways to improve but also because it made me appreciate the environment I work in and the hassles we avoid by (somewhat) decent naming standards. We had a saying in the Navy that "every rule is written in blood" and I'm certainly glad to learn these naming rules from those that preceded me and not from pulling out my hair at work.