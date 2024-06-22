this is also from react conf. 

## Rule of react
1. Components and hooks must be idempodent
2. Side effects must run outside of render
3. Props and state are immutable
4. Return values and arguments to hooks are immutable
5. values are immutable after being passed to JSX

Mero bujyai ma react compiler le chai 
react app optimize garda rule of react sabbai bhako code ma jaha jaha useMemo thapnu parney ra aaru optimization hooks thapnu parney tyaha tesle thyakkai thapdincha ani aaru kura chai tala cha.. tara i don't know shit. :)

In the talk a compiler was made which can:
1. analyze memoization
2. analyze mutability
3. analyze aliasing
4. analyze (re)assignment
5. understood control flow
6. codegen JS
7. optimize memoization

