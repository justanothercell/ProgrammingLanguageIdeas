# ProgrammingLanguageIdeas

Gradually designing the perfect general purpose programming lanuage

### What Should Be Noted And Is Probably Best:
- the less special cases the better: <br>
    syntactic sugar should be able to be converted to a "lower-level" form and not be a black-box-compiler-special-case.
- give control to the programmer: <br>
    be able to override keywords, nothing hardcoded if possible (similar to bullet point 1)
- learning curve: <br>
    of course a own syntax is ok, but nothing too crazy that makes people not want to use it. Keep it "normal".
- interface to existing stuff: <br>
    We dont want to code everything for a std lib manually (for example be bale to call java classes if we run it on jvm)
- good compiler/error message experience
- self hosted, apart from the vm (obviously)
- typesafe (please. please. please.)
