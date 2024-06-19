### Linked list
-> 
```
type List<A> = Nil | Cons<A>

interface Nil {
	readonly _tag: 'Nil'
}

interface Cons<A>{
	readonly _tag : 'Cons'
	readonly head: A
	readonly tail: List<A>
}

const nil: List<never>= {type: 'Nil'}

const cons = <A>(head: A, tail: List<A>): List<A> = ({
	_tag: 'Cons',
	head,
	tail
})
```

