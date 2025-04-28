---

# 1. 📚 Custom Hook in React — Notes

### What is a Custom Hook?
- A **Custom Hook** is a **JavaScript function** whose name **starts with `use`** and that **calls other hooks** inside it.
- It helps to **reuse stateful logic** (like data fetching, form handling, etc.) between components **without duplicating code**.

---

### Why use Custom Hooks?
- **Code Reusability**: Write once, use anywhere.
- **Cleaner Components**: Move complex logic out of the component.
- **Separation of Concerns**: Keeps UI and business logic separate.
- **Testability**: Custom hooks can be easily unit-tested.

---

### How to Create a Custom Hook?

Basic syntax:
```javascript
import { useState } from 'react';

function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  const increment = () => setCount(prev => prev + 1);
  const decrement = () => setCount(prev => prev - 1);
  const reset = () => setCount(initialValue);

  return { count, increment, decrement, reset };
}
```

**Usage in a Component**:
```javascript
function CounterComponent() {
  const { count, increment, decrement, reset } = useCounter(5);

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
      <button onClick={reset}>Reset</button>
    </div>
  );
}
```

---

### Rules for Custom Hooks
- Must start the function name with `use`.
- Must only call React hooks inside it (`useState`, `useEffect`, etc.).
- Must follow the **Rules of Hooks** (call at the top level, not inside loops, conditions, or nested functions).

---

### Real-world Examples
- `useFetch` → Data fetching hook.
- `useForm` → Handling form data and validations.
- `useAuth` → Authentication logic management.
- `useDebounce` → Debounce input values.

---

# 2. 🎯 Interview Questions and Answers on Custom Hook

---

### Q1. What is a custom hook in React?

**Answer**:  
A custom hook is a reusable JavaScript function in React that starts with the word `use` and can call other hooks inside it. It lets you reuse stateful logic across multiple components without repeating code.

---

### Q2. Why do we need custom hooks?

**Answer**:  
Custom hooks help in **reusing logic** across components, making components **simpler and more readable**. They also encourage **separation of concerns** and **improve code maintainability**.

---

### Q3. What are the rules to follow while creating a custom hook?

**Answer**:
- The hook’s name must start with `use`.
- Only call hooks at the top level (not inside loops, conditions, or nested functions).
- Only call hooks from React functions (functional components or other hooks).

---

### Q4. Can custom hooks use other custom hooks?

**Answer**:  
Yes! A custom hook can call other custom hooks. This promotes further modularization and reusability of logic.

---

### Q5. How are custom hooks different from React components?

**Answer**:  
- **Custom Hooks** are **functions** that manage stateful logic and side effects.
- **Components** are responsible for rendering UI.
- Hooks cannot return JSX; components do.

---

### Q6. Give an example of a scenario where you would create a custom hook.

**Answer**:  
When multiple components need the same logic, like **fetching data from an API**, you would create a `useFetch` custom hook to avoid duplicating the fetch logic in each component.

---

### Q7. How do custom hooks improve testability?

**Answer**:  
Since custom hooks are just functions that manage state or effects, they can be unit-tested independently from UI, making the business logic easier to verify.

---

### Q8. Can custom hooks accept arguments?

**Answer**:  
Yes, just like any JavaScript function, a custom hook can accept parameters to customize its behavior (e.g., `useCounter(initialValue)`).

---

# Bonus: ✨ Example of a simple `useFetch` Custom Hook

```javascript
import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    async function fetchData() {
      try {
        const response = await fetch(url);
        const json = await response.json();
        setData(json);
      } catch (error) {
        console.error('Error fetching data:', error);
      } finally {
        setLoading(false);
      }
    }
    fetchData();
  }, [url]);

  return { data, loading };
}
```

---
