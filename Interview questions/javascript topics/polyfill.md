##### forEach polyfill

```
const arr = [1,2,3,4,5];

arr.forEach((el) => console.log(el));

function printSth(el) {
	console.log(el);
}

Array.prototype.myForEach = function (cb) {
	console.log("this", this);
	for(let index = 0; index < array.lenth; index++){
		cb(this[index]);
	}
}

arr.myForEach(printSth)

```

### map polyfill

```
const arr = [1,2,3,4,5];

  

Array.prototype.myMap = function (cb) {

let res = []

for(let index = 0; index < this.length; index++){

res.push(cb(this[index]))

}

return res;

}

const res = arr.myMap((el) => el * 2)

console.log(res)
``````
