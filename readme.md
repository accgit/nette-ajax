## Info
Simple js plugins for Nette Framework AJAX.

## Auto Refresh
For some applications, we may need an automatic refresh page, which we can do subsequently.

```js
function startAutoRefresh() {
	refresh = setInterval(function(){
		$.nette.ajax({
			url: {link refresh!},
		});
	}, 10000);
}
```

In cases where we need to call other js components and in the background we perform automatic page refresh, it will be necessary to stop refresh in this case. This is the case for modal windows.

```js
function stopAutoRefresh() {
	clearTimeout(refresh);
}
```

Once the request is complete, we'll call the automatic page refresh feature again.
