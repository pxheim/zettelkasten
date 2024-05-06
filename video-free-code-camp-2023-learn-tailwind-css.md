https://www.youtube.com/watch?v=ft30zcMlFao

[[$Videos]]

# Colors

You can add colors to stuff by simply typing `text-green` or `bg-green-500`.

You can add your own colors by editing `tailwind.config.js`:

```js
[...]
  theme: {
    extend: {
      colors: {
	    myColor: {
	      100: "#123456",
	      200: "2345678",
	      [...],
	    }
	  }
    }
  }
```

Make sure you add these into extend, otherwise you will lose all the colors already provided by tailwind. You might want this behavior though.

# Customization

Modifiers for breakpoints can be prefixed to other classes, e.g. `text-sm` will always apply, but `lg:text-lg` will only apply to large screens. You can add custom screens and modify their sizes in tailwind config.

Spacing can also be modified to be whatever you want. Spacing is used in classes like `mb-1` referring to margin bottom w/ a spacing of 1, which by default is 8px.

You can add arbitrary variables into your classes if you have one-off things, e.g. `text-[#123456]`.

You can create custom css classes using a combination of tailwind classes by using the `@apply` directive. E.g.

```css
.card {
  @apply text-white;
  @apply text-xl;
}
```