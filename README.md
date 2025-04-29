# `cn` Utility Function 🧩

A lightweight utility to simplify conditional and merged Tailwind CSS class management using `clsx` and `tailwind-merge`.

## ✨ Features

- Combines `clsx` and `tailwind-merge` in one reusable function.
- Helps manage dynamic class names cleanly and efficiently.
- Prevents conflicting Tailwind classes from being applied.
- Improves readability of component styling logic.

## 📦 Installation

You can simply copy the `cn.ts` file into your utilities folder.

```ts
// utils/cn.ts
import { clsx, type ClassValue } from "clsx";
import { twMerge } from "tailwind-merge";

export const cn = (...inputs: ClassValue[]) => twMerge(clsx(inputs));
```

#### Make sure to install the required dependencies:

```bash
npm install clsx tailwind-merge
```

`or`

```bash
bun add clsx tailwind-merge
```

# 🚀 Usage

Import and use cn in your components to conditionally and cleanly apply Tailwind CSS classes.

### ✅ Basic Example

```ts
import { cn } from "@/utils/cn";

export default function Button({ isPrimary }: { isPrimary?: boolean }) {
  return (
    <button
      className={cn(
        "px-4 py-2 rounded text-white",
        isPrimary ? "bg-blue-500" : "bg-gray-500"
      )}
    >
      Click Me
    </button>
  );
}
```

## 🧠 Use Case: Conditional Classes

```tsx
<div className={cn("p-4", isDarkMode && "bg-black text-white")} />
```

## 🧹 Use Case: Tailwind Class Conflict Resolution

Tailwind doesn't allow multiple conflicting classes like `p-2` and `p-4` — `tailwind-merge` ensures only the correct one is applied:

```tsx
cn("p-2", "p-4"); // ➝ "p-4"
```

## 🧱 Use Case: Combining Static + Dynamic Classes

```tsx
const isActive = true;
const classes = cn("text-sm font-medium", isActive && "text-blue-500");

<div className={classes}>Link</div>;
```

## 💡 Why use `cn`?

- ✅ Clean code: Avoid messy ternaries and long string concatenations.
- ✅ Tailwind-aware: Automatically handles class conflicts like `bg-red-500` vs `bg-blue-500`.
- ✅ Readable: Makes UI components easier to understand and maintain.

## 📁 File Structure Suggestion

Place this utility in a shared utilities folder:

```css
src/
├── components/
├── pages/
├── utils/
│   └── cn.ts

```

## 📜 License

MIT License. Free to use and modify.
Happy coding! 🚀

---

###### Chaile ami ekta logo/cover image o design kore dite pari ei utility er jonno. Chao?

---
