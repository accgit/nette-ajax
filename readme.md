## Info
Simple js extensions for Nette Framework AJAX. Adapted to Bootstrap 4

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

## Modal extension
Basic start and close of modal.

```js
$.nette.ext('nette.modal', {
	success: function (payload) {

		// Run the modal window with the command.
		if (payload.modal === 'run') {

			// Disable closing the modal after clicking outside it.
			$('#modal').modal({
				backdrop: 'static',
				keyboard: false
			});

		// Exits the modal with the command.
		} else if (payload.modal === 'close'){
			$('#modal').modal('hide');

			// Deletion of inserted classes after calling a modal.
			$('body').removeClass('modal-open');
			$('.modal-backdrop').remove();
		}
	}
});
```

## Form submit
Send a form using enter or a reader that sends enter.

```js
$.nette.ext('nette.submit', {
	load: function() {
		$('#form').off('keypress').on('keypress', function(e) {
			if (e.which === 10 || e.which === 13) {
				$(this).submit();
			}
		});
	}
});
```
