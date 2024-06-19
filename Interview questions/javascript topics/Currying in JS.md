A functional programming technique that involves breaking down a function that takes multiple arguments into a series of function that take one argument

### example
```
function add (a){
	return function (b){
		return function (c){
				return a + b + c;
			}
		}
}
```

### Use-case: Automated email server
```
function setAutoEmail(to){
	return function (subject){
		return function (body){
				console.log(`Send email to ${to} for the subject: ${subject} about ${body}`)
			}
		}
}

let result = setAutoEmail("test@gmail.com")
let step2 = result("New Order Confirmation")
setp2("hey gaurv, there is something for you.")
```
#### Use-case II: Processing the order for the client
```
const addCustomer = fn => (...args) => {
        console.log('Saving customer info...')
        return fn(...args)
}

const processOrder = fn => (...args) => {
        console.log(`Processing order #${args[0]}`)
        return fn(...args)
}

let completeOrder = (...args) => {
        console.log(`Order #${[...args].toString()}`)
}
completeOrder = processOrder(addCustomer)
console.log(completeOrder("21"))

```