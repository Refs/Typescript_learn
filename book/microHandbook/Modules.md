

## Simple Example

```ts
import { StringValidator } from "./Validation";
import { ZipCodeValidator } from "./ZipCodeValidator";
import { LettersOnlyValidator } from "./LettersOnlyValidator";

// Some samples to try
let strings = ["Hello", "98052", "101"];

// Some samples to try
let strings = ["Hello", "9833", "101"];

// Validators to use
let validators: {[s:string]: StringValidator} = {};
validators["ZIP code"] = new ZipCodeValidator();
validators["Letters only"] = new LettersOnlyValidator();

// validators string类的属性 所引用的是StringValidator类的实例对象；即制定的都是类别，而现实中则都是实例；

```

## Optional Module Loading and Other Advanced Loading Scenarios

```ts
declare function require(moduleName: string): any;

import {ZipCodeValidator as Zip} from "./ZipCodeValidator";

if () {
    let ZipCodeValidator: typeof Zip = require("./ZipCodeValidator");
    let validator = new ZipCodeValidator();
    
}

```



> 一般来说，一个C文件应该是一个模块,如果你的程序仅仅有一个模块（仅仅一个C文件），就可以不用建立H文件了。否则你的模块肯定不是独立的，你的模块里面的实现要被别的模块调用。这个时候你最好生成一个头文件(H文件)，在头文件里面可以声明你的那些函数是公共的。当别的模块包含你的头文件后，就可以使用你的公共声明了。

```ts
// from the consumption side, the consumer of any given module gets to pick the name that they will use to refer to the module, so accidental nameing conflits are impossible.

// we have written a small set of simplistic string validators, as you might write to check a user's input on a form in a webppage or check the the format of an 
```

```ts
interface StringValidator {
    isAcceptable(s: string): boolean;
}

let lettersRegexp = /^[A-Za-z]+$/;
let numberRegexp = /^[0-9]+$/;

class LettersOnlyValidator implements StringValidator {
    isAcceptable(s: string){
        return lettersRegexp.test(s);
    }
}

class ZipCodeValidator implements StringValidator{
    isAcceptable(s: string) {
        return s.length === 5 && numberRegexp.test(s);
    }
}


let strings = ["Hello","878","234"];

let validators : {[s: string]:StringValidator} = {};

validators["ZIP code"] = new ZipCodeValidator();
valodators["Letters only"] = new LettersOnlyValidator();

for (let s of strings){
    for(let name in validators){
        let isMatch = validators[name].isAcceptable(s);

    }
}

// as we add more validators, we are going to want to have some kind of organization scheme so that we can keep track of our types and not worry about name collosions with other objects. instead of putting lots of different names into the global namespace , let's wrap up opur objects into a namesapce.

// Notice that we don't use the require keywords, instead we assign directly from the qualified name of the symbol we're importing. 

// this is simliar to using var, but also works on the type and

// the refernce tag here allow us to locate the declaaration file that contains the declaration for the ambient module. this is 

// To reiterate why you shouldn't try to namespace your module contents, the general idea of namespacing is to provide logical grouping of constructs and to prevent name collosions. Because the module file itself is already a logical grouping, and its top-level name is defined by the code that imports it ,it's unnecessary to use an additional module layer for exported objects.

// One effect of this is that it's not possible to concatenate module source files depending on the module system you target. 

// we could define each module in its own .d.ts file with top-level export declarations, but it's more convenient to write them as one larger .d.ts file. to do so , we use a construct similar to ambient namespaces, but we use the module keywords and quoted name of the

// Consider a project configration where only some modules are available in one location, and the rest are in another.

// this tells the compiler for any module import that matvhs the pattern "*" , to look in

// this tells the compiler for any module import that matches the pattern, to look in two locations.

// 1、pattern '* is matched and wildcard capture the whole module name.
// 2. try firt substitution in hte list: '*' -> folder1/file2
// 3.result of substitution is non-relative name - combine it with BaseUrl 
// 4. file exists. Done
```

