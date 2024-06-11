### Debounce or, Throttle

Debounce :
At end of wait time
Final State
The best way to put is when your app need to execute a function or, say API Calls after user do something like text input. You use Debounce

Throttle
At  intervals 
intermediate state
When you want something happen in a same interval of time

### example: Button click and, scrolling window
```
const initApp = () => {
  const tbutton = document.querySelector("#throttle");
  tbutton.addEventListener("click", throttle(clickLog, 2000));
  window.addEventListener("scroll", throttle(scrolling, 2000));
};

const clickLog = () => console.log("click");
const scrolling = () => console.log("scrolling");

document.addEventListener("DOMContentLoaded", initApp);

const throttle = (fn, delay) => {
  let lastTime = 0;
  console.log("Called Throttle Immediately");
  let id = 0;
  return (...args) => {
    const now = new Date().getTime();
    id++;
    if (now - lastTime < delay) return;
    lastTime = now;
    console.log(`event id: ${id}`);
    fn(...args);
  };
};

```