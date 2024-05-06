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
