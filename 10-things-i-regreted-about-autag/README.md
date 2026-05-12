# 10 Things I Regreted About Autag (probably more)

No one cares Autag (only i know), isn't Node.js but anyway,
Autag is a CLI than generate some boilerplate, i make this thing
like 5 years ago when i started to code, so i uploaded to npm, get
like _~1000 total downlods in this period_, and _~450 as highest
weekky downlods_ and ,_~23 versions_, i know, im the next react, although
it's fine to was created when i have like one year to start coding, but
also, it's so probably than the 80% or even more of downloads, aren't
humans, probably are bots or when i tested because was used the **npx**
command to test new versions, but it's werid too, because the highest
weekly downloads was in 2025, and i leave the proyect like 4 years ago,


[Autag NPM Page](https://www.npmjs.com/package/autag)
(I don't think you wanna inatall it (not works now for something
with a deprecated dependency),  but you wanna see how shit is)

So, who i make this blog? Basically i was checked my olds repos because 
i was bored, and... see some things... isn't only shit code 
(i expected this), but i really don't expected the things i see,
to be honest, hurt me a bit.

## 1. Who is this variable?
### Why is shit?
The rest of things i known than was tried seems profesional programmer
or just i make pettry bad code in this age, but this, genuinily i
don't get who i try it, serously, it's too pointenless and my only
theory is think than this line of code, was necesary to classes can work or
can be exported in Node.js, so, who hurt me so much? Basically ahead
of each class i add a variable called ```global_object```:
```js
let global_object = new Object()
class Some {}
```
also when i make this, use the ```module.exports = Some```, so also
with this name refering to global object, i sure than i think it's
necesary to export, especially, for some reason use the Object constructor 
insted of just ```{}```, i tried to use decorators when no even exist
(currently still not event exist)
### How to stop being shit
Just not use this stupid variable anymore, also check well the docs
and undersatade any line of code, because if not understall at all
can make things like this, adding pointeless boilerplate.

## 2. Insane errors managment
### Why is shit?
At least i tried manage the errors but for this type of management,
was better doing nothing, so, context... for some commands of my CLI
i use file system (fs) of Node.js, in this momemnt i don't know it why
is a promise and old methods use callbacks, so, who is the form i manage
the errors as professinal:
```js
fs.readFile("file.txt", "utf-8", error => {
    if (error) console.log(error)
})
```
### How to stop being shit


## 3. Over eginer
### Why is shit?
My proyect have like 13 commands, are simple commands, so the best option is
just make a file per command, so i make exaclty this when i working in this
shit no? well... i make something so much professional and clean, one folder
per command, and a ```normal.js``` to handle the command logic and a ```global.js``` 
than exports the hanlder.
```txt
|__ functions/
|_____ command/
|________ global.js
|________ normal.js
```
To expand professionalism, i use a ultra neceaary class (with the 
```global_object``` thing of course), example of one of the maaterprice i make:
```js
const { normalRemove } = require('./normal.js')

let global_object = new Object();
class removeManager {
    constructor(){}

    normal(){
        normalRemove();
    }
}

module.exports = removeManager;
```
Void constructor, method than only call a function, definitivily a perfect
implemented class.
But don't end here, to make it even more clean, i have a ```export.js``` file
than export into a object all methods.
```js
module.exports = {
    initManager: require('./functions/init/global.js'),
    fileManager: require('./functions/file/global.js'),
    ignoreManager: require('./functions/ignore/global.js'),
    licenseManager: require('./functions/license/global.js'),
    mkdirManager: require('./functions/mkdir/global.js'),
    translateManager: require('./functions/translate/global.js'),
    renameManager: require('./functions/rename/global.js'),
    removeManager: require('./functions/remove/global.js'),
    readManger: require('./functions/read/global.js'),
    localManager: require('./functions/local/global.js'),
    renderManager: require('./functions/render/global.js'),
    copyManager: require('./functions/copy/global.js'),
    minifyManager: require('./functions/minify/global.js'),
    searchManager: require('./functions/search/global.js')
 }
```
Yep, still don't end.
```js
const fs = require('fs');
const { initNormal } = require('./functions/init/normal.js');
if (!fs.existsSync('.autag')) initNormal();
const autag = require('./export.js');
const file = new autag.fileManager();
const ignore = new autag.ignoreManager();
const license = new autag.licenseManager();
const mkdir = new autag.mkdirManager();
const translate = new autag.translateManager();
const rename = new autag.renameManager();
const remove = new autag.removeManager();
const read = new autag.readManger();
const local = new autag.localManager();
const render = new autag.renderManager();
const copy = new autag.copyManager();
const minify = new autag.minifyManager();
const search = new autag.searchManager();
const inquirer = require('inquirer');
```
### How to stop being shit
7

## 4. if/else managment
### Why is shit?
```js
fs.readFile(`${anweser.file}`, 'utf-8', (error, data) => {
    if (error) console.log(error);
    if (data.includes(anweser.text)) {
        console.log(true);
    } else {
        console.log(false);
    }
});
```
I need explain it how a ```console.log(data.includes(anweser.text))``` was better?
Also, te file use a too neceaary template string instaed of just push the
```anweser.text``` here. Probably had more things like this, but this
is the most inecesary probably.
### How to stop being shit
This is a pettry obvius bad boolean uses

## 5. DRY master
### Why is shit?
This is the main reason because this proyect have so much lines than need 
it, there have things like:
```js
inquirer.prompt([
    {
        key: "file",
        value: "file"
    },
    {
        key: "ignore",
        value: "ignore"
    },
    {
        key: "mkdir",
        value: "mkdir"
    }
    /* rest of necesary code options */
])
```
This is the worst case of this and, genually i don't know why not just
use a ```["file", "ignore", "mkdir", ...]```
```js
if (anweser.lang === "en") {
    translate(anweser.data, {
        to: anweser.lang
    }).then(res => {
        console.log(`translate to english:\n${res.text}`)
    })
}
if (anweser.lang === "es") {
    translate(anweser.data, {
        to: anweser.lang
    }).then(res => {
        console.log(`translate to spanish:\n${res.text}`)
    })
}
```
This case to:
```js
inquirer.prompt([
    {
        name: "paste",
        message: "Write a file to paate content"
    },
    {
        name: "copy",
        message: "Write a file to copy content"
    }
])
```
In this case could be use a helper than generte object ```{name, message}```
bassed in an a ```string[]```
### How to stop being shit

## 6. This break the proyect
### Why is shit?
Just one dependency breaks all proyect. For some reason, in a tool than 
works to make/edit files and folders, i add a option to can translate 
text usign some Google translate API, yes, no have any sense than this 
exist in this proyect, but also, this makes the CLI **unitilizable** now,
because (pack) was deleted from npm
### How to stop being shit
First, no add nothing than don't import, is just stupid bloatware and in
free proyects no have any sense, you can make marketing about stupid thing
than no one imports, more code and functions makes tye code more unsafe 


## 7. Version controlling
### Why is shit?
Like 22 versions and v3.2.2 now, this is just because i'm make so many
mistakes and i fixed low time diff, like, all 22 of this versions, was
maked in like 3 months or even less (or more, maybe just have bad memory)
### How to stop being shit
Before making a serius proyect (or at least a proyect than try it), search
who is SemVer and center on no have so many versions, is better a one good
update per moth than 4 bad updates in a month.

## 8. Perfect english
### Why is shit?
Some context, i don't talk english as first language, so probably this
super important and serius blog, had so many errors with my translation,
but the important thing it's than my current english, is better than in
Autag, so if you see bad english, don't worry, remember than is not
than bad as Autag, because in Autag, basically so many versions are:
```docomentation fix```, like 20 of 22 versions contains some of fix docs
translate, even the majory of updates are just this, fixes, even the code
has variables like "anwesers", keep in like 80% of code
### How to stop being shit
I could be said than just learn english better, but even now, not dominated
at 100%, currently is undesrtable at least, but anyways, it's so sure than this blog
had so many errors in my english, so i can't burlarme de mi esta vez.

## 9.Obessed for some reason
### Why is shit?
Basically the amounts of downlods was to important to my in this age,
still remember how 3..6 times i checked the npm page to can see the
downlods, even remember how when i get a the big amount of ~150 downlods, 
i was in my peak of satisfaction. The problem with this is reduce the quality
becuase how i was keep my community active (probably 90% of this downlods was
bots), i realese so many versions in low time
### How to stop being shit


## 10. Logo
### Why is shit?
Is just so ugly, it's so obvius than was maked for a kid in paint, supposed
to be an gear, but is more like a gray egg with a black cross on center
!(autag_logo)[assets/autag_logo]
### How to stop being shit
I can't, is just so ugly so try fixed, i can't fixed.
