
1. Binary search algorithm
```
// 
export default function bs_list(haystack: number[], needle: number): boolean {
    let lo = 0
    let hi = haystack.length 
    while (hi > lo) {
        const m = Math.floor( lo + (hi - lo)/2)
        if(haystack[m] === needle){
            return true;
        } else if (haystack[m] > needle){
            hi = m
        } else {
            lo = m + 1
        }
    } ;
    return false
}	
```

2. Two Crystal Ball Problem

```
// O(sqrt(N)) -> Big O
export default function two_crystal_balls(breaks: boolean[]): number {

    const jmpAmount = Math.floor(Math.sqrt(breaks.length));
    let i = jmpAmount;
    for (; i < breaks.length; i += jmpAmount) {

      if (breaks[i]) {
        break;
      }
    }
    i -= jmpAmount;

    for (let j = i; j < breaks.length; j++) {
        if (breaks[j]) {
        return j;
      }
    }
    return -1;
}

```