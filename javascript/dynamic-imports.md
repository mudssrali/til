# Dynamic Imports

Use dynamic import only when necessary. The static form is preferable for loading initial dependencies, and can benefit more readily from static analysis tools and `tree shaking`.

To dynamically import a module, the `import` keyword may be called as a function. When used this way, it returns a `promise`.

```js
import('/modules/my-module.js')
  .then((module) => {
    // Do something with the module.
  })
```

Or you can use `await`

```js
 let module = await import('/modules/my-module.js')
```

**Example:**

```js
const main = document.querySelector("main")
for (const link of document.querySelectorAll("nav > a")) {
  link.addEventListener("click", (e) => {
    e.preventDefault()

    import('/modules/my-module.js')
      .then(module => {
        module.loadPageInto(main)
      })
      .catch(err => {
        main.textContent = err.message
      })
  })
}
```