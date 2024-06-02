---
title : Asynchronous Delays in JavaScript Crafting a Simple sleep() Function

tags: javascript

---
<div>

# Asynchronous Delays in JavaScript: Crafting a Simple sleep() Function {#asynchronous-delays-in-javascript-crafting-a-simple-sleep-function .p-name}

</div>

::: {.section .p-summary field="subtitle"}
JavaScript lacks a built-in sleep() function, unlike certain other
programming languages. Nevertheless, it is possible to craft one...
:::

::::::::::: {.section .e-content field="body"}
:::::: {#1f65 .section .section .section--body .section--first}
::: section-divider

------------------------------------------------------------------------
:::

:::: section-content
::: {.section-inner .sectionLayout--insetColumn}
### Asynchronous Delays in JavaScript: Crafting a Simple `sleep()`{.markup--code .markup--h3-code} Function {#d0de .graf .graf--h3 .graf--leading .graf--title name="d0de"}

#### JavaScript lacks a built-in sleep() function, unlike certain other programming languages. Nevertheless, it is possible to craft one effortlessly by utilizing Promises and setTimeout(). This guide will walk you through the process of creating a sleep() function and shed light on why setTimeout() does not promptly run the provided code. {#39bb .graf .graf--h4 .graf-after--h3 .graf--subtitle name="39bb"}

To create a `sleep()`{.markup--code .markup--p-code} function, we\'ll
leverage JavaScript\'s Promise API. Here\'s how you can do it:

``` {#dd9d .graf .graf--pre .graf-after--p .graf--trailing .graf--preV2 code-block-mode="2" spellcheck="false" code-block-lang="javascript"}
function sleep(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}
```
:::
::::
::::::

:::::: {#f604 .section .section .section--body .section--last}
::: section-divider

------------------------------------------------------------------------
:::

:::: section-content
::: {.section-inner .sectionLayout--insetColumn}
This `sleep()`{.markup--code .markup--p-code} function takes a single
argument, `ms`{.markup--code .markup--p-code}, which represents the
number of milliseconds you want the program to pause. It returns a
Promise that resolves after the specified delay.

It's easy to use the `sleep()`{.markup--code .markup--p-code}function
with async/await syntax.

``` {#b1c9 .graf .graf--pre .graf-after--p .graf--preV2 code-block-mode="2" spellcheck="false" code-block-lang="javascript"}
async function test() {
  console.log('Start');
  await sleep(2000); // Sleep for 2 seconds Zzzz
  console.log('End');
}

test();
```

Let's do the same this time with `setTimeout()`{.markup--code
.markup--p-code}

`setTimeout()`{.markup--code .markup--p-code} schedules a function to be
executed after a specified delay, but it **does not stop** the execution
of the rest of your code. Some people might expect that
`setTimeout()`{.markup--code .markup--p-code} will pause the execution
of the code until the specified time has passed, but that\'s not how it
works. Here is an example where running `setTimeout()`{.markup--code
.markup--p-code} alone might **not** behave as expected :

``` {#aff2 .graf .graf--pre .graf-after--p .graf--preV2 code-block-mode="1" spellcheck="false" code-block-lang="javascript"}
console.log('Start');

setTimeout(() => {
  console.log('after 2 seconds');
}, 2000);

console.log('End');
```

If you expect `setTimeout()`{.markup--code .markup--p-code} to pause the
code execution until the time has passed, you might think the output
should be :

``` {#b090 .graf .graf--pre .graf-after--p .graf--preV2 code-block-mode="1" spellcheck="false" code-block-lang="sql"}
Start
after 2 seconds
End
```

But in reality...

``` {#ef23 .graf .graf--pre .graf-after--p .graf--preV2 code-block-mode="1" spellcheck="false" code-block-lang="sql"}
Start
End
after 2 seconds
```

To achieve behavior similar to pausing execution, we must use
`async/await`{.markup--code .markup--p-code} with a custom
`sleep()`{.markup--code .markup--p-code} function:

``` {#92d4 .graf .graf--pre .graf-after--p .graf--preV2 code-block-mode="1" spellcheck="false" code-block-lang="javascript"}
function sleep(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function test() {
  console.log('Start');
  await sleep(2000); // Sleep for 2 seconds Zzzz
  console.log('after 2 seconds');
  console.log('End');
}

test();
```

Output :

``` {#304a .graf .graf--pre .graf-after--p .graf--preV2 code-block-mode="1" spellcheck="false" code-block-lang="sql"}
Start
/* Program will sleep for 2 seconds */
after 2 seconds
End
```

`setTimeout()`{.markup--code .markup--p-code} schedules code to run
after a delay but does not pause the execution of subsequent code. To
achieve a pause or delay in execution, use `async/await`{.markup--code
.markup--p-code} with a custom `sleep()`{.markup--code .markup--p-code}
function. This way, you can control the timing of your code more
effectively.
:::
::::
::::::
:::::::::::

By [Iqwertzuiop](https://medium.com/@iqwertzuiop){.p-author .h-card} on
[May 25, 2024](https://medium.com/p/92ee53bd23f2).

[Canonical
link](https://medium.com/@iqwertzuiop/asynchronous-delays-in-javascript-crafting-a-simple-sleep-function-92ee53bd23f2){.p-canonical}

Exported from [Medium](https://medium.com) on June 2, 2024.
