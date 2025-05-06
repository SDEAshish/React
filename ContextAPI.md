
### What is Context API?

* React’s **Context API** allows you to **share state globally** across the component tree **without prop drilling**.
* It is used to pass data from parent to deeply nested children **without manually passing props at each level**.

---

### When to Use Context?

Use Context when:

* You have **global state** like user authentication, theme, language, etc.
* **Props drilling becomes unmanageable** (passing data through many components just to reach a child).
* You want to **avoid Redux** for simple global state needs.

---

### 🔧 Basic Steps to Use Context API

1. **Create Context**

```javascript
import { createContext } from 'react';
export const ThemeContext = createContext();
```

2. **Provide Context**

```javascript
function App() {
  const theme = 'dark';

  return (
    <ThemeContext.Provider value={theme}>
      <MyComponent />
    </ThemeContext.Provider>
  );
}
```

3. **Consume Context**

```javascript
import { useContext } from 'react';
import { ThemeContext } from './ThemeContext';

function MyComponent() {
  const theme = useContext(ThemeContext);
  return <div>The current theme is: {theme}</div>;
}
```

---

### 🔁 What can you store in Context?

* Strings, numbers, booleans
* Arrays, objects
* Functions (like toggleTheme)
* Even entire components or hooks

---

### Real-world Use Cases

* User authentication (`AuthContext`)
* Theme switching (`ThemeContext`)
* Multi-language support (`LocaleContext`)
* Cart or shopping context (`CartContext`)

---

# 🎯 Context API Interview Questions and Answers

---

### Q1. What is the Context API in React?

**Answer**:
Context API is a built-in React feature used to pass data across the component tree without having to manually pass props down at every level.

---

### Q2. Why and when would you use Context API?

**Answer**:
Use it when you have **global data** (like theme, user info, etc.) that needs to be accessible by **many components at different levels** in your app, especially to avoid **prop drilling**.

---

### Q3. How do you create and use context in React?

**Answer**:

1. Create context using `createContext()`.
2. Wrap your component tree with `Context.Provider` and provide a `value`.
3. Use `useContext()` to access that value inside any component.

---

### Q4. What are the performance concerns with Context API?

**Answer**:

* When the context value changes, **all components using that context will re-render**, even if they don’t use the changed part.
* To solve this, use **memoization**, **context splitting**, or **selectors**.

---

### Q5. How is Context API different from Redux?

| Context API             | Redux                                   |
| ----------------------- | --------------------------------------- |
| Built-in                | External library                        |
| Simple and minimal      | More complex, powerful                  |
| Good for small apps     | Best for large-scale apps               |
| No middleware           | Supports middleware (e.g., Redux Thunk) |
| No dev tools out-of-box | Excellent dev tools                     |

---

### Q6. Can you update context values?

**Answer**:
Yes, usually you pass both the value and an updater function:

```javascript
<ThemeContext.Provider value={{ theme, setTheme }}>
```

And in a consumer:

```javascript
const { theme, setTheme } = useContext(ThemeContext);
setTheme('light');
```

---

# 🧠 Quick Summary for Context API

* Avoids prop drilling ✅
* `createContext()` to define ✅
* `.Provider` to supply ✅
* `useContext()` to consume ✅
* Good for auth, theme, and global state ✅

---
