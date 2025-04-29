# _`cn`_ – Tailwind CSS Class Combiner

![cn Tailwind Class Combiner](./cn-cover.png)

---

A utility function that simplifies combining and conditionally applying Tailwind CSS classes using [`clsx`](https://www.npmjs.com/package/clsx) and [`tailwind-merge`](https://www.npmjs.com/package/tailwind-merge).

## ✨ Features

- Clean and readable class composition
- Conditional styling with `clsx` logic
- Intelligent class conflict resolution with `tailwind-merge`
- Tiny and dependency-light
- Works with strings, booleans, arrays, and object syntax

## 📦 Installation

1. Copy the utility:

   ```ts
   // utils/cn.ts
   import { clsx, type ClassValue } from "clsx";
   import { twMerge } from "tailwind-merge";

   export const cn = (...inputs: ClassValue[]) => twMerge(clsx(inputs));
   ```

2. Make sure to install the required dependencies:

   ```bash
   npm install clsx tailwind-merge
   ```

   `or`

   ```bash
   bun add clsx tailwind-merge
   ```

---

## 🚀 Usage

Import and use cn in your components to conditionally and cleanly apply Tailwind CSS classes.

**Basic Example**:

```tsx
import { cn } from "@/utils/cn";

const Button = ({ primary }: { primary?: boolean }) => {
  return (
    <button
      className={cn(
        "px-4 py-2 rounded",
        primary ? "bg-blue-500 text-white" : "bg-gray-300 text-black"
      )}
    >
      Click me
    </button>
  );
};
```

<br/>

## 🧠 Examples & Use Cases

1. Conditional Boolean Classes

   ```tsx
   <div className={cn("font-medium", isActive && "text-blue-500")} />
   ```

2. Using Object Syntax (clsx feature)

   ```tsx
   <div
     className={cn("p-4", {
       "bg-red-500": isError,
       "bg-green-500": isSuccess,
       "text-white": isError || isSuccess,
     })}
   />
   ```

3. Conflict Resolution (tailwind-merge feature)

   ```tsx
   cn("p-2", "p-4"); // → "p-4"
   cn("text-sm", "text-lg"); // → "text-lg"
   cn("bg-blue-500", "bg-red-500"); // → "bg-red-500"
   ```

4. Merging Static + Conditional

   ```tsx
   cn(
     "flex items-center gap-2",
     isDarkMode && "bg-gray-900 text-white",
     isRounded && "rounded-full"
   );
   ```

5. With Arrays (spread patterns)

   ```tsx
   const classes = ["text-sm", isActive && "text-blue-500"];
   cn(...classes); // → "text-sm text-blue-500"
   ```

6. Reusable Component Example

   ```tsx
   type InputProps = {
     hasError?: boolean;
     disabled?: boolean;
     className?: string;
   };

   const Input = ({ hasError, disabled, className }: InputProps) => {
     return (
       <input
         disabled={disabled}
         className={cn(
           "px-3 py-2 border rounded-md outline-none transition",
           {
             "border-red-500 bg-red-50": hasError,
             "opacity-50 cursor-not-allowed": disabled,
           },
           className
         )}
       />
     );
   };
   ```

7. Use with Tailwind group, peer, focus, etc

   ```tsx
   cn(
     "peer px-4 py-2 border",
     isInvalid && "border-red-500",
     "focus:outline-none focus:ring-2 focus:ring-blue-500"
   );
   ```

---

## 📁 File Structure Suggestion

```css
src/
├── app/
├── components/
├── lib/
│   └── utils/
│       └── cn.ts

```

## 🤔 Why Use This?

- 🧠 Avoid messy ternaries and string concatenation
- 🛠️ Tailwind-aware: resolves conflicting utilities automatically
- 💅 Keeps JSX/TSX clean and easy to read
- 🔁 Reusable across the entire codebase

## 📜 License

MIT License — `use freely in personal or commercial projects`

---

<h3 align="center">Happy coding! 🚀</h3>

---
