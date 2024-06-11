# Arrays Methods(concat, filter, map, reverse, …spread, sort, slice) — immutable arrays usage in JS/React

Level: Moderate
ID: ACJ-4
Last edited time: August 7, 2023 11:55 AM
Status: Not started

all the methods here avoid mutation by returning a new array. that is most preferred way to write code to avoid bugs

TOC: 

1. {concat, spread syntax (to add an array)}, 
2. {filter, slice (to remove an array)},
3. {map (to replace an array)},
4. {reverse and sort, by copying the array first (to sort the array)}

let arr = [];

### recommended methods to use in arrays

1. iterator
    
    ```jsx
    const arr = ["a", "b", "c"];
    const li = [''];
    for(const letter of arr){
    	li = letter;
    }
    ```
    
2. concat - add two arrays
    
    ```jsx
    const array1 = ['a', 'b', 'c'];
    const array2 = ['d', 'e', 'f'];
    const array3 = array1.concat(array2);
    
    console.log(array3);
    // Expected output: Array ["a", "b", "c", "d", "e", "f"]
    ```
    
    ```jsx
    import { useState } from 'react';
    
    let nextId = 0;
    
    export default function List() {
      const [name, setName] = useState('');
      const [artists, setArtists] = useState([]);
    
      return (
        <>
          <h1>Inspiring sculptors:</h1>
          <input
            value={name}
            onChange={e => setName(e.target.value)}
          />
          <button onClick={() => {
            setArtists([
              ...artists,
              { id: nextId++, name: name }
            ]);
          }}>Add</button>
          <ul>
            {artists.map(artist => (
              <li key={artist.id}>{artist.name}</li>
            ))}
          </ul>
        </>
      );
    }
    
    //expected output
    // a form adding never stuffs to array 
    ```
    
3. filter - remove arrays elements
    
    ```jsx
    const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
    
    const result = words.filter((word) => word.length > 6);
    
    console.log(result);
    // Expected output: Array ["exuberant", "destruction", "present"]
    
    //Search in an array
    const fruits = ["apple", "banana", "grapes", "mango", "orange"];
    
    /**
     * Filter array items based on search criteria (query)
     */
    function filterItems(arr, query) {
      return arr.filter((el) => el.toLowerCase().includes(query.toLowerCase()));
    }
    
    console.log(filterItems(fruits, "ap")); // ['apple', 'grapes']
    console.log(filterItems(fruits, "an")); // ['banana', 'mango', 'orange']
    ```
    
    ```jsx
    //react usage
    import { useState } from 'react';
    
    let initialArtists = [
      { id: 0, name: 'Marta Colvin Andrade' },
      { id: 1, name: 'Lamidi Olonade Fakeye'},
      { id: 2, name: 'Louise Nevelson'},
    ];
    
    export default function List() {
      const [artists, setArtists] = useState(
        initialArtists
      );
    
      return (
        <>
          <h1>Inspiring sculptors:</h1>
          <ul>
            {artists.map(artist => (
              <li key={artist.id}>
                {artist.name}{' '}
                <button onClick={() => {
                  setArtists(
                    artists.filter(a =>
                      a.id !== artist.id
                    )
                  );
                }}>
                  Delete
                </button>
              </li>
            ))}
          </ul>
        </>
      );
    }
    ```
    
4. slice - it also remove arrays elements
    
    ```jsx
    const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
    const citrus = fruits.slice(1, 3);
    
    // fruits contains ['Banana', 'Orange', 'Lemon', 'Apple', 'Mango']
    // citrus contains ['Orange','Lemon']
    ```
    
    ```jsx
    //react usage
    
    ```
    
5. map - replace the array elements
    
    ```jsx
    //using map() on sparse arrays
    console.log (
    	[1, , 3].map((x, index) => {
    		console.log(`Visit ${index}`)
    		return x * 2;
    })
    )
    
    // visit 0
    // visit 2
    // [2, empty, 6]
    ```
    
    ```jsx
    //react usage
    import { useState } from 'react';
    
    let initialCounters = [
      0, 0, 0
    ];
    
    export default function CounterList() {
      const [counters, setCounters] = useState(
        initialCounters
      );
    
      function handleIncrementClick(index) {
        const nextCounters = counters.map((c, i) => {
          if (i === index) {
            // Increment the clicked counter
            return c + 1;
          } else {
            // The rest haven't changed
            return c;
          }
        });
        setCounters(nextCounters);
      }
    
      return (
        <ul>
          {counters.map((counter, i) => (
            <li key={i}>
              {counter}
              <button onClick={() => {
                handleIncrementClick(i);
              }}>+1</button>
            </li>
          ))}
        </ul>
      );
    }
    ```
    
6.  use reverse and sort - copy the array first and - basically to sort arrays

```jsx
import { useState } from 'react';

let nextId = 3;
const initialList = [
  { id: 0, title: 'Big Bellies', seen: false },
  { id: 1, title: 'Lunar Landscape', seen: false },
  { id: 2, title: 'Terracotta Army', seen: true },
];

export default function BucketList() {
  const [myList, setMyList] = useState(initialList);
  const [yourList, setYourList] = useState(
    initialList
  );

  function handleToggleMyList(artworkId, nextSeen) {
    setMyList(myList.map(artwork => {
      if (artwork.id === artworkId) {
        // Create a *new* object with changes
        return { ...artwork, seen: nextSeen };
      } else {
        // No changes
        return artwork;
      }
    }));
  }

  function handleToggleYourList(artworkId, nextSeen) {
    setYourList(yourList.map(artwork => {
      if (artwork.id === artworkId) {
        // Create a *new* object with changes
        return { ...artwork, seen: nextSeen };
      } else {
        // No changes
        return artwork;
      }
    }));
  }

  return (
    <>
      <h1>Art Bucket List</h1>
      <h2>My list of art to see:</h2>
      <ItemList
        artworks={myList}
        onToggle={handleToggleMyList} />
      <h2>Your list of art to see:</h2>
      <ItemList
        artworks={yourList}
        onToggle={handleToggleYourList} />
    </>
  );
}

function ItemList({ artworks, onToggle }) {
  return (
    <ul>
      {artworks.map(artwork => (
        <li key={artwork.id}>
          <label>
            <input
              type="checkbox"
              checked={artwork.seen}
              onChange={e => {
                onToggle(
                  artwork.id,
                  e.target.checked
                );
              }}
            />
            {artwork.title}
          </label>
        </li>
      ))}
    </ul>
  );
}
```

Lists of methods that mutates the array

to add: push, unshift

to remove: pop, shift, splice

to replace: splice.arr[i] = …

to sort: reverse, sort

## Using Immer (use-immer)

Immer just create a proxy or, let’s say a draft state (draft) which is copied leaving the original array stale. Meaning, immer always constructs the next state from scratch according to the changes done to the draft. 

```jsx
//react use-case
import { useState } from 'react';
import { useImmer } from 'use-immer';

let nextId = 3;
const initialList = [
  { id: 0, title: 'Big Bellies', seen: false },
  { id: 1, title: 'Lunar Landscape', seen: false },
  { id: 2, title: 'Terracotta Army', seen: true },
];

export default function BucketList() {
  const [myList, updateMyList] = useImmer(
    initialList
  );
  const [yourList, updateYourList] = useImmer(
    initialList
  );

  function handleToggleMyList(id, nextSeen) {
    updateMyList(draft => {
      const artwork = draft.find(a =>
        a.id === id
      );
      artwork.seen = nextSeen;
    });
  }

  function handleToggleYourList(artworkId, nextSeen) {
    updateYourList(draft => {
      const artwork = draft.find(a =>
        a.id === artworkId
      );
      artwork.seen = nextSeen;
    });
  }

  return (
    <>
      <h1>Art Bucket List</h1>
      <h2>My list of art to see:</h2>
      <ItemList
        artworks={myList}
        onToggle={handleToggleMyList} />
      <h2>Your list of art to see:</h2>
      <ItemList
        artworks={yourList}
        onToggle={handleToggleYourList} />
    </>
  );
}

function ItemList({ artworks, onToggle }) {
  return (
    <ul>
      {artworks.map(artwork => (
        <li key={artwork.id}>
          <label>
            <input
              type="checkbox"
              checked={artwork.seen}
              onChange={e => {
                onToggle(
                  artwork.id,
                  e.target.checked
                );
              }}
            />
            {artwork.title}
          </label>
        </li>
      ))}
    </ul>
  );
}
```