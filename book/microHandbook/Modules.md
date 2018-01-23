

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