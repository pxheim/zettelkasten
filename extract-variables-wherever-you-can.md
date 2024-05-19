Extracting variables is done in order to make your code read better. E.g. instead of hardcoding a number into your method, your code is more likely to read like prose if you extract the variable. E.g. 

```ts
if (item.abv > 4.7) {
	sendToVinmonopolet();
}
```

is much easier to understand if you write:

```ts
if (alcoholLimitExceedsGroceryStoreLimit) {
	sendToVinmonopolet();
}
```
