Why use typescript?

1. ensures program works as expected by avoiding the obvious mistakes


How typechecking occurs?

1. Typescript source > Typescript AST 
2. AST is checked by typechecker 
3. Typescript AST > Javascript source


How Js works?

1. Js source > AST
2. AST > bytecode
3. bytecode evaluated by runtime

What is Js engine?

Js compiler and runtime is smushed into a single program called the Js engine.
ex: V8 for chrome, node js , opera
spidermonkey for firefox
chakra for edge
JSCore for safari

What is a type system?
A set of rules that a typechecker uses to assign types to your program.
Two types of type system - 1. explicit annotation (value: type : let one : number = 1) 2. infer (let a =  1)


What is the difference between Js type system and typescript type system?
- How types are bound?
JS - Dynamically
Ts - Statically
- Are types automatically converted?
JS - yes
TS - mostly no
- When are types checked?
JS - at runtime
TS - at compilation time
- When are erros surfaced?
JS - mostly runtime
TS - mostly compile time

//todo
Which module system should TSC compile your code to (CommonJS, SystemJS, ES2015, etc.)?

How would you kick start a typescript project?
1. Install typescript, types for typescript and a tslint
2. configure the tsconfig.json for src, destionation folders, module structure etc
3. configure the tslint json. edit recommended rules if needed.
4. create a ts file and enter something.
5. compile the code using node_modules/.bin/tsc
6. run the compiled code using node index.js 
