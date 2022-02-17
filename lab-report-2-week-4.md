---
layout: default
---

# Lab Report 2 – Week 4
## Incremental Programming and Debugging +
### Best Practices in version control and committing individual bug fixes
> **Lab overview and tasks:**
# ヽ༼ ಠ益ಠ ༽ﾉ
>>In this blog post, we will cover how to use sample **Failure-inducing input** *(..(⚆ᗝ⚆)..inducing tears)* and how to cope ಥ_ಥ with debugging. I'm joking, but even so - it is totally common to get frustrated with debugging from time to time. A good thing you will likely pick up from this course is the sense that *attitude* weighs **heavy** when it comes to debugging *else* you run the risk of breaking your code further **-and-** to learn to start small (incremental programming) so you can start smart :) 
>>Check this [article](https://jvns.ca/blog/debugging-attitude-matters/) provided in lab for example:

<img src="https://pbs.twimg.com/media/EVfh7xaXsAAJa3E?format=jpg&amp;name=large">

>> Laying it all on the table 
┬─┬ノ(ಠ_ಠノ) ... we see there are more approachable ways to debugging and moreover there are the typical yet misconceived approaches to avoid. Refer to the END of the page for more debug reads provided in the course :)

# ┬┴┬┴┤ᵒᵏ (･_├┬┴┬┴
***

### Getting Started
Before we can begin, you might want to have this [starter code](https://github.com/ucsd-cse15l-w22/markdown-parse) in hand - it will be easier to follow along with the clips as you pause and try getting some outout of your own :)
To get a quick idea of what this ```Markdown Parser``` is supposed to do, check out the short clip below:
<video src="assets\images\week4.intro.mp4" controls="controls" style="max-width: 1000px;"></video>
As of now, the program can read-in a simple.md file as a parameter and will attempt to retrieve all the links found in the given file. **HOWEVER** - as we progress through the labs, we will need to evolve the code to handle **any** or **all** markdown files, and return only the links and nothing else from the give file(s).
> Moving on, we will learn the approach of *incremental programming* and proactive *debugging* - by assessing the expectations of the program, starting with **Failure-inducing inputs**. In this case, these will be 3 simple, yet unique test.md files that categorize, as well as reveal individual **symptoms**. Hopefully this systematic approach will help us understand and address any *faulty logic* in our code as we build-UP. 
>> (**bugs** = *logic errors* in a program that causes it to operate incorrectly[**symptoms**], but does not terminate abnormally or crash) 
**déjà vu** Σ(-᷅_-᷄๑) *did i just create a link above*

For more reference - link over to this vid from Joe as he walks us through the creation of this program. Hopefully this will give you better intuition of the starter code's base logic and methods

^.ᆽ.^=∫ [Markdown Parsing Starter Code](https://youtu.be/_y9hkrN9k3w)

### Intro Vid: encountering bugs
<video src="assets\images\testCase1.mp4" controls="controls" style="max-width: 1000px;"></video>

### Bug fix #1
#### The infinite loop -
<div class="gallery">
    <div class="img-container">
      <img
        src="assets\images\Fix1-diff.png"
        alt="Fix 1 - Diff"
        data-original="Fix1-diff.png"
      />
    </div>
  </div>
<!-- <img src="assets\images\Fix1-diff.png" alt="" width="1000"/> -->

[test-&alpha;.md](https://github.com/jhugomagana/markdown-parse/blob/fc35e33c774cf910f3ea9fabb9a518fa10283651/test-A.md)
```
## Bug *&alpha;*
In the initial test-file.md case, we only demonstrated that our code can read in a file as a parameter -and- the code's basic recognition of: 
+ [inline-style links](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links)
+ [one more link](https://some-other-link.com)
one of many formats for including Markdown links.
>However, what would happen if we were to add a body of text before and after the last recognizable link like we just did now ...
>Refer to the comment block notes in MarkdownParse.java associated with this commit to see working solution for this bug.
## END
```
>Symptom observed:
<img src="assets\images\testCase_alpha_infinite_loop.png" alt="" width="1000"/>
<img src="assets\images\testCase_alpha_bug.png" alt="" width="1000"/>
<img src="assets\images\testCase_alpha_solution.png" alt="" width="1000"/>
### Bug fix #2
#### True links vs image links -
<img src="assets\images\Fix2-diff.png" alt="" width="1000"/>

[test-&beta;.md](https://github.com/jhugomagana/markdown-parse/blob/fc35e33c774cf910f3ea9fabb9a518fa10283651/test-B.md)
```
## Bug *&beta;*
In the initial test-file.md case, we only demonstrated that our code can read in a file as a parameter -and- the code's basic recognition of: 
>[inline-style links](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links)
>[one more link](https://some-other-link.com)

Similarly to `links` in markdown - images are almost identical in format - for example:
>![link](https://github.com/jhugomagana/cse15l-lab-reports/blob/main/assets/images/i_am_Link.jpg?raw=true)
If you were to see the markdown format of this image, it nearly identical to link format but with an "!" preceding the `[]` brackets.
## EOF
```
>![link](https://github.com/jhugomagana/cse15l-lab-reports/blob/main/assets/images/i_am_Link.jpg?raw=true)

>Symptom observed:
<img src="assets\images\testCase_beta_confuses_images.png" alt="" width="1000"/>
<img src="assets\images\testCase_beta_solution.png" alt="" width="1000"/>

### Bug fix #3
#### Defining true links even further -
<img src="assets\images\Fix3-diff.png" alt="" width="1000"/>

[test-&gamma;.md](https://github.com/jhugomagana/markdown-parse/blob/fc35e33c774cf910f3ea9fabb9a518fa10283651/test-G.md)
```
## Bug *&Gamma;*
So far, our parser demonstrates basic recognition of,
>[inline-style links](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links)
And can distinguish against the similar looking image formatting that uses an `!` preceeding its square brackets `[]` 

>if you noticed above - I am using these square brackets to highlight an example
- in this case, not all brackets are used exclusively for linking
- as well as not all parenthesis are used solely for linking and are regularly used in standard body of text to hold an example or commentary...

> For example, these (paired parenthesis) are still coupled to the last recognized square brackets.
> The parser then may get confused and display unexpected symptoms. 
## EOF
```
>Symptom observed:
<img src="assets\images\testCase_gamma_bug.png" alt="" width="1000"/>
<img src="assets\images\testCase_gamma_solution.png" alt="" width="1000"/>


***
<audio preload="metadata" controls loop autoplay>
  <source src="assets\images\Battle! (Wild Pokémon) medley (Gen 1 - Gen 8) - Arranged by DeadmanPR (128 kbps).mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>