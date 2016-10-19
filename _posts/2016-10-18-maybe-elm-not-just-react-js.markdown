---
layout: post
title: "'Maybe' Elm, Not 'Just' React.js"
categories: elm react redux functional reactive javascript
abstract: "Try out Elm, a functional reactive programming language"
author: Jon Sharratt
hero_image: blog_wework_office.png
hero_image_alt: "Panorama of WeWork office, Old St."
---

Our experience working with many current clients using React.js and Redux architecture we find that starting up a new project means new choices of exciting tech and new libraries.

What comes with that is (albeit healthy) team discussions and debates about how a project should be structured and what portion of new tech to try out.  There are core concepts that have started to crop up for every many of the web apps we deliver that make up what we want from our modern web app architecture.  All of which can be achieved using the plethora of JavaScript modules npm provides (for better or for worse, fatigue anyone?).

Below is a list of these core concepts that we believe make up a modern web application architecture today. We have noted down some of the popular JavaScript libraries / frameworks used (at the time of writing ;)).

### Core Concepts

##### User Interface
Declarative views that can be re-used and that are easy to debug.

[React.js](https://facebook.github.io/react/)

##### Typed
Easier to maintain, refactor and less buggy code before runtime.

[Flow](https://github.com/facebook/flow)

##### Module Loading
Encapsulate code into single units of work.

[Babel: Transform ES2015 Modules](http://babeljs.io/docs/plugins/transform-es2015-modules-commonjs/)

**Side note:**

Babel presets also required in order to have latest language syntax to make our developer experience better.

##### Predictable State / Immutability
Predictable state management with often better performance.

[Mori](https://github.com/swannodette/mori) | 
[Immutable.js](https://github.com/facebook/immutable-js/)

##### Functional Reactive Programming
Simplify managing asynchronous events over time.

[cycle.js](http://staltz.com/xstream/) | 
[RxJS](http://reactivex.io/rxjs/) | 
[xstream](http://staltz.com/xstream/)

### Elm
> "A delightful **language** for reliable webapps."
>
> Evan Czaplicki Sept - 1st [efc02cc7](https://github.com/elm-lang/elm-lang.org/commit/239634b491b07461eb7b90f565ad8034e09cca78#diff-efc02cc79e4da914bfcf4748f4648174R32)

As the quote suggests from Elms creator Evan Czaplicki it aims to combine the best of breed modern day web app architecture in the form of an entirely new, enjoyable, and almost pure functional language coupled with an incredible compiler and tooling.  At the end of the day it all boils down into a language we are used to, JavaScript ;o)!

Having started to use Elm in one of our on going open source projects ([ui for yith](https://github.com/craftship/yith-ui)) and getting to grips with its syntax we noticed that there is a slight learning curve.  If you are not familiar with statically typed languages, functional programming and reactive concepts it really does make it an enjoyable challenge.

**If you take one thing away from this article, let it be this.  Stick with the initial learning curve of Elm.  You and your team will not regret it!**

If you break the back and get into the language you very quickly realise you are in the hands of a fantastically well thought out language and developer experience.  The natural destination of where you are heading is a day of being more productive, with better quality code coupled with a serious amount of confidence in your work.

##### Typed

Built-in support for type annotations as well as type inference.  This is where the star of the show kicks in, the compiler.  Error messaging and debug information of coding mistakes happens before runtime.  NoRedInk where Evan Czaplicki the creator of Elm currently works claim to have been using it **in production over a couple of years with 0 runtime errors**.  Just impressive to say the least.

##### Module Loading

Built-in support for modules with convention based naming meaning there is only really one way modules get written / structured within your application.  Supports explicit exposure of functions to ensure optimised bundle.

##### Predictable State / Immutability

All values in Elm are immutable by default coupled with persistent data structures.

##### Functional Reactive Programming

Elm is a functional reactive programming language, there is no framework or library required.  Built from the ground up it is almost a pure functional language and is closely related to a language such as Haskell.

For reactivity, all events are carried over **Signals** which you then can apply relevant transforms.  For things like HTTP asynchronous operations **Tasks** can be used when an operation can succeed **or** fail.  Elm comes with what is known as ['The Elm Architecture'](https://guide.elm-lang.org/architecture/) to jump start your applications based on these built-in concepts.

### Great Developer Experience Extras

##### Elm Format
[GitHub](https://github.com/avh4/elm-format)

A community standard to allow you to format your Elm code as you save your files in your favourite editors, very much inspired by Go langs formatter.  As Elm is still quite an early language the majority if not all code bases use this formatter.  Check out other projects / libraries and instantly read with ease.

Stop your team thinking about how to format your code and let a tool do it for you (the way it should be).  Focus on effectively building a great product with new and interesting features.

##### Elm Package Management
[Elm Packages](http://package.elm-lang.org/)

An npm like package manager for all things awesome in Elm to help you build out your application.  One major feature that is very welcome is as the language is statically typed it can **enforce** semver.

This is great for the community of packages being published and gives incredible confidence in your usage and planning of module updates.


### In Summary

So when you start looking into your next web project.  Don't just think of grabbing your default `npm init` and `npm i` tooling, maybe give Elm a try.  We are convinced teams will fall in love with what is shaping up to be a fantastic modern day language for the web.

Check out this awesome post on [How to use Elm at Work](http://elm-lang.org/blog/how-to-use-elm-at-work) or [get in touch](hello@craftship.io) with us to see how we can help.
