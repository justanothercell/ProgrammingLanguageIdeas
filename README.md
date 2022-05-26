# ProgrammingLanguageIdeas

Gradually designing the perfect general purpose programming lanuage. <br>
No guarantee that that is all even possible with a compiled language, im just tossing stuff around. <br>
THe first version of this was just written with the browser github editor onto the main branch, so, yes very professionally done and totally not unstructured

### Contributing:
make an issue, make a pr, explain your idea directly, anythign goes! You just have to convince me that your idea is an improvement and ill either add it or add it as an alternative option.

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
- self hosted compiler
- typesafe (please. please. please.)

### Compiler
- Compiled to bytecode/machinecode/... not interpreted please
- be able to print out the AST / tokens / any intermediate form at any step to console/file. if possible, also make loading from these steps from file possible
- make parts (like tokenizer) as modular and usable in other contexts as possible, so people can just use that and dont need to do it themselves
- suggestions mode: give hints on what coudl eb the solution to the current problem
- interactive mode: like suggestions mode, but on error the compiler guides you through a multiple choice dialog (command line), tutorial-style, option to print the docs for a problem on demand, etc, make the amount of information variable

### REPL and stuff
- only if it's possible to code that without having to implement an interpreter additionally to the compiler
- stuff like python's exec() and eval(), but safe (note buttet point 3 under Compiler)

### Syntax etc:
- curly braces, java style (c# style looks a bit better, but 1 extra line everytime u use it? nope!)
- semicolons or not? idk? whatever is chosen, stick to it and make it mandatory (no optional ; *cough cough* js)
- types: inferred if possible, var keyword (decide upon a best practice and stick to it, dont mix var-style with explicit type style, use the other one sparingly)
- (suggestion, not final): {class: PascalCase, function: PascalCase, field_of_any_kind_seriously_c_sharp_i_hate_how_its_different_every_time: camelCase}
- types: python seems cool but idk how well it fits, probably the normal style...
- return types: both java and python stype have their pros and cons, i'd be with python, just because fun and seems more reusable :)
- make classes and funcs be passed around as arguments just by writing them without the braces (like python)
- no new keyword *hard decicion, but seems the right thing to do, no final decicion*
- annotations: much talk is needed, because annotations work differently everywhere
- generics: some sort of generic "This" to reference the "current class", for singletons/builders etc. are generics even needed when u can pass classes as arguments? is that compatible?
