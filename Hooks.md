# 📚 Hooks in React — Full Notes

---

### What are Hooks?
- **Hooks** are special **functions** that let you **use React features** (like state, lifecycle methods, context) **inside functional components**.
- **Introduced in React 16.8** to make functional components more powerful (earlier only class components could have state, lifecycle).

---

### Why were Hooks introduced?
- To **reuse stateful logic** across components.
- To avoid **complex class components** (e.g., `this` keyword confusion).
- To make **components smaller and cleaner**.

---

### 🛠️ Commonly Used React Hooks

| Hook          | Purpose                                                            |
|---------------|---------------------------------------------------------------------|
| `useState`    | Manage **state** inside a functional component                     |
| `useEffect`   | Handle **side effects** (API calls, DOM updates, etc.)              |
| `useContext`  | Use **Context API** data inside a component                        |
| `useRef`      | Access and persist **mutable references** (DOM nodes or variables) |
| `useMemo`     | **Optimize performance** by memoizing expensive calculations       |
| `useCallback` | **Optimize function references** to prevent unnecessary renders    |
| `useReducer`  | Alternative to `useState` for **complex state management**          |
| `useLayoutEffect` | Like `useEffect` but runs **before** browser paint (rare use)  |
| `useImperativeHandle` | Customize the instance value that is exposed to parent    |

---

# ✨ Basic Examples of Important Hooks

---

### 1. `useState` — Add state to functional component
```javascript
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  
  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```

---

### 2. `useEffect` — Perform side effects (like fetching data)
```javascript
import { useEffect, useState } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(res => res.json())
      .then(setData);
  }, []); // [] => run only once after component mounts

  return <div>{JSON.stringify(data)}</div>;
}
```

---

### 3. `useContext` — Access context data
```javascript
import { useContext } from 'react';
import { ThemeContext } from './ThemeProvider';

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return <button style={{ background: theme.background }}>Click me</button>;
}
```

---

# 🎯 Hooks Interview Questions and Answers

---

### Q1. What are React Hooks?

**Answer**:  
Hooks are special functions that let you use state, side effects, context, and other React features inside functional components.

---

### Q2. What are the rules for Hooks?

**Answer**:
- Hooks must start with `use` (e.g., `useState`, `useEffect`).
- Hooks can only be called at the **top level** of a component or another hook (not inside loops, conditions, nested functions).
- Hooks must be called **only inside React functions** (functional components or custom hooks).

---

### Q3. Can Hooks be used inside class components?

**Answer**:  
No. Hooks are designed **only for functional components**.

---

### Q4. What is the difference between `useEffect` and `useLayoutEffect`?

**Answer**:  
- `useEffect` runs **after** the render is painted to the screen.
- `useLayoutEffect` runs **before** the paint — useful for synchronously measuring layout (very rare, and can block rendering if not careful).

---

### Q5. When would you use `useMemo` and `useCallback`?

**Answer**:
- `useMemo`: To **memoize the result** of expensive computations.
- `useCallback`: To **memoize the function** itself so that it doesn’t get recreated on every render.

---

### Q6. What is `useReducer`, and when would you use it?

**Answer**:  
- `useReducer` is used for **more complex state logic** where state transitions depend on previous state values or involve multiple sub-values.
- It is similar to `redux` reducer but inside a component.

Example:
```javascript
const [state, dispatch] = useReducer(reducer, initialState);
```

---

### Q7. What is a Custom Hook?

**Answer**:  
A custom hook is a function that uses React hooks to create reusable logic across components. Its name must start with `use`.

---

# 🧠 Quick memory tip:  
- `useState` = data  
- `useEffect` = side effects  
- `useContext` = global values  
- `useRef` = mutable storage  
- `useMemo/useCallback` = optimization  
- `useReducer` = complex state logic

---
