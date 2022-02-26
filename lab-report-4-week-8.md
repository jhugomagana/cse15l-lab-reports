---
layout: default
---

# Lab Report 4 – Week 8
## Sample markdown snippets and further testind:

> **Lab overview and tasks:**
>>For each snippet, add a test both to your implementation of markdown-parse, and the implementation you reviewed. Run the tests and show the results of running the tests on each.
Answer the following questions with 2-3 sentences each:
Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.
Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.
Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.

# ┬┴┬┴┤ᵒᵏ (･_├┬┴┬┴
***

### Snippet 1
```html
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

### Snippet 2
```html
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```

### Snippet 3
```html
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
    https://ucsd-cse15l-w22.github.io/
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```


***
<audio preload="metadata" controls loop autoplay>
  <source src="assets\images\Tower of Lahja - Ninja Gaiden II_ The Dark Sword of Chaos (128 kbps).mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>