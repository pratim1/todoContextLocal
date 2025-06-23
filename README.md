// The addTodo function is responsible for adding a new todo item to the existing list of todos. Let me break it down simply:
// javascriptconst addTodo = (todo) => { 
//   setTodos((prev) => (  
//     [{id: Date.now(), ...todo}, ...prev] 
//   ))   
// }
// What it does:

// Takes a todo parameter: This is the new todo object that needs to be added (like {todos: "Buy groceries", completed: false})
// Uses setTodos to update state: setTodos is the state setter function that updates the todos array
// Uses previous state: (prev) => gives access to the current/previous state of todos array
// Creates new array: [{id: Date.now(), ...todo}, ...prev] creates a completely new array with:

// First element: A new todo object that combines:

// id: Date.now() - generates a unique ID using current timestamp
// ...todo - spreads all properties from the incoming todo object


// Rest of elements: ...prev spreads all existing todos after the new one



// Example:
// If current todos = [{id: 2, todos: "Study", completed: false}]
// And you call addTodo({todos: "Exercise", completed: false})
// Result: [{id: 1640995200000, todos: "Exercise", completed: false}, {id: 2, todos: "Study", completed: false}]
// The new todo gets added to the beginning of the array, so it appears first in the list.



>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>    delete fn
javascriptconst deleteTodo = (id) => {
  setTodos((prev) => prev.filter((todo) => todo.id !== id))
}
<!-- 1. Function receives parameter:

id = ID of the todo we want to DELETE (example: 2)

2. setTodos((prev) => - Get current todos array

prev = current todos array, like:

javascript[
  {id: 1, todos: "Study", completed: false},
  {id: 2, todos: "Exercise", completed: true},    // ← We want to DELETE this
  {id: 3, todos: "Sleep", completed: false}
]
3. prev.filter((todo) => - Loop through each todo

filter() creates a new array with only items that pass the test
It checks each todo one by one

4. todo.id !== id - The filter condition

This is the test each todo must pass to stay in the array
!== means "not equal to"
We want to keep todos whose ID is NOT the one we want to delete

Loop Example (deleting id = 2):
First todo: {id: 1, todos: "Study", completed: false}

Test: 1 !== 2 → TRUE → Keep it ✓

Second todo: {id: 2, todos: "Exercise", completed: true}

Test: 2 !== 2 → FALSE → Remove it ✗

Third todo: {id: 3, todos: "Sleep", completed: false}

Test: 3 !== 2 → TRUE → Keep it ✓

Final Result:
javascript[
  {id: 1, todos: "Study", completed: false},
  {id: 3, todos: "Sleep", completed: false}
]
Key Points:

filter() keeps items where condition is TRUE
!== means "not equal to"
Logic: "Keep all todos EXCEPT the one with this specific ID"
Result: The todo with matching ID gets removed, all others stay -->