## Типові JavaScript задачі на співбесіді
### Reverse String
```
function reverseString(str) {
    return str
        .split("")
        .reverse()
        .join("");
}

console.log(reverseString("hello"));    \\olleh
```
---
### Remove Duplicates
```
function removeDuplicates(arr){
    return [
        ...new Set(arr)
    ];
}
```

```
function removeDuplicates(arr){
    return arr.filter(
        (item,index)=>{
            return arr.indexOf(item) === index;
        }
    );
}
```
---
### Frequency Counter
```
function frequencyCounter(arr){
    const counter = new Map();
    for(const item of arr){
        counter.set(
            item,
            (counter.get(item) || 0) + 1
        );
    }
    return counter;
}
```
---
### Find Max / Min
```
const max = Math.max(...numbers);
```
---
