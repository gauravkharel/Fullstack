A debouncing function is an adv. js concept which allows us to have a delay to execute certain function even if the event happened tons of time. The best debouncing lib I have seen is Rx.js and, it is uses for fetching data as per the need and, handling events simultaneously.
### Basic Example
This illustrated the time delay in button as how many time you click you end up executing the callback only once. 
```
const intApp = () => {
  const button = document.querySelector('.button');
  button.addEventListener("click", debounce(clickLog, 2000));
};
const clickLog = () => console.log("clicked");

document.addEventListener("DOMContentLoaded", intApp);

const debounce = (fn, delay) => {
  let id;
  console.log(`id at immediate load: ${id}`);
  return (...args) => {
    console.log(`previous id: ${id}`);
    if (id) clearTimeout(id);
    id = setTimeout(() => {
      fn(...args);
    }, delay);
  };
};

```

#### The use cases
- Search box suggestions
- text field auto-saves
- eliminating double button clicks

### Use case I: Search box suggestion
```
<input type="text" id="search-box" placeholder="Type to search...">
<div id="results"></div>

<script>
const searchBox = document.getElementById('search-box');
const results = document.getElementById('results');

const fetchResults = debounce(function(query) {
  // Simulate an API call
  results.innerText = `Searching for: ${query}`;
  console.log(`Fetching results for: ${query}`);
}, 300);

searchBox.addEventListener('input', (event) => {
  fetchResults(event.target.value);
});
</script>

```

### Use Case II: Window Resize
```
window.addEventListener('resize', debounce(function() {
  console.log('Window resized');
  // Add your resize handling code here
}, 200));

```

Use Case III: Using debouncing with react

```
const Input = () => {
  const [value, setValue] = useState("initial");

  // memoize the callback with useCallback
  // we need it since it's a dependency in useMemo below
  const sendRequest = useCallback((value: string) => {
    console.log("Changed value:", value);
  }, []);

  // memoize the debounce call with useMemo
  const debouncedSendRequest = useMemo(() => {
    return debounce(sendRequest, 1000);
  }, [sendRequest]);

  const onChange = (e) => {
    const value = e.target.value;
    setValue(value);
    debouncedSendRequest(value);
  };

  return <input onChange={onChange} value={value} />;
}

```

Another example IV: Using useRef for debouncing
```
const ref = useRef(debounce(() => {

    // this value is coming from state

    console.log(value);

  }, 500));
```

In JS objects are **not** [immutable](https://developer.mozilla.org/en-US/docs/Glossary/Immutable). Only primitive values, like numbers or references to objects, will be “frozen” when a closure is created. If in our “frozen” `sendRequest` function I will try to access `ref.current`, which is by definition mutable, I will get the latest version of it all the time!

Usecase V: useDebounce hook
```
const useDebounce = (callback) => {
  const ref = useRef();

  useEffect(() => {
    ref.current = callback;
  }, [callback]);

  const debouncedCallback = useMemo(() => {
    const func = () => {
      ref.current?.();
    };

    return debounce(func, 1000);
  }, []);

  return debouncedCallback;
};
```

Eg usecase of useDebounce hook
```
const Input = () => {
  const [value, setValue] = useState();

  const debouncedRequest = useDebounce(() => {
    // send request to the backend
    // access to latest state here
    console.log(value);
  });

  const onChange = (e) => {
    const value = e.target.value;
    setValue(value);

    debouncedRequest();
  };

  return <input onChange={onChange} value={value} />;
}
```

