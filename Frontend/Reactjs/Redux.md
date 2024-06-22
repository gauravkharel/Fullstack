3 principles:
1st: The global state of your application is stored as an object inside a single store.
2nd: The only way to change the state is to dispatch an action, an object that describes what happened. Only action let redux to change states.
3rd: To specify how the state tree is updated based on actions, you write pure renders. 

Reducer(prevState, action) -> newState
