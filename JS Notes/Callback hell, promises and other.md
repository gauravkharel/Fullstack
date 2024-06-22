Callback hell: when callbacks after callbacks/inside callbacks happens
- which makes code unreadable and unmanageable

Inversion of control:
- Callback calling other callback create dependency which loose control of the callback functions. 

Promises: 
- Promises are immutable, resolved only once.
- Promise object is a placeholder for a certain period of time until user receives a value from asynchronous operation.
- The treatment for inversion of control
- From MDN -> The promise object represents the eventual completion (or, failure) of an asynchronous operation and it's resulting value.

Promise chaining:
```
createOrder(cart)
	.then(function(orderId){
		return proceedToPayment(orderId)
	})
	
```

#### The three states of promises
Pending, fulfilled, rejected