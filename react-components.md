# React Component Agent Skills

This document defines practical skills for a coding agent focused on creating, organizing, and maintaining React components in a scalable codebase.

## Core principles

- Follow the Single Responsibility Principle: each component should have one clear purpose, which improves reuse, testing, and maintainability.
- Prefer composition over large monolithic components, building features from smaller pieces that work together cleanly.
- Keep component hierarchies explicit so parent components coordinate data flow while child components focus on smaller UI responsibilities.
- Avoid “god components” that mix rendering, business logic, data fetching, and state updates in one file.

## Component creation skills

### 1. Break UI into focused components
- Identify distinct visual and behavioral responsibilities in a screen before writing code.
- Split large interfaces into smaller reusable parts such as layout, form fields, lists, rows, cards, and actions.
- Name components by domain intent and role, for example `UserCard`, `PaymentForm`, or `ProductRow`.

### 2. Design for composition
- Build components so they can be combined without forcing rippling changes across the codebase.
- Use props, `children`, and controlled extension points to support flexible composition.
- Favor reusable building blocks over duplicated JSX across pages and features.

### 3. Separate UI from logic
- Keep presentational components focused on rendering and interaction display.
- Move data fetching, transformation, and orchestration into container components or custom hooks when complexity grows.
- Reduce coupling by passing prepared data and callbacks into display components through clear props.

### 4. Keep state minimal
- Place state at the lowest level that still supports the required behavior.
- Avoid unnecessary re-renders by managing state efficiently and only where it is needed.
- Prefer stateless or minimally stateful components when a component only renders data from props.

## Organization skills

### 5. Create a predictable folder structure
- Use a simple, consistent project structure so components are easy to find, debug, and extend.
- Group files either by feature or by component responsibility, but apply one system consistently.
- Keep related files close together, such as component, test, styles, story, and local hook files.

Example feature-oriented structure:

```text
src/
  features/
    dashboard/
      components/
        StatsCard.tsx
        ActivityFeed.tsx
      hooks/
        useDashboardData.ts
      DashboardPage.tsx
      index.ts
  shared/
    components/
      Button/
        Button.tsx
        Button.test.tsx
        index.ts
```

### 6. Organize reusable components by scope
- Put globally reusable UI primitives in a shared components area.
- Keep feature-specific components inside their feature folders to avoid accidental cross-feature coupling.
- Consider Atomic Design only when the team benefits from that vocabulary and the system is design-heavy.

### 7. Use barrel exports carefully
- Add `index.ts` files to simplify imports and define the public surface of a folder.
- Export only stable, intended modules to avoid leaking internal implementation details.
- Prefer explicit exports over wildcard exports when a folder contains many internal helpers.

## Quality skills

### 8. Enforce consistency
- Use consistent naming conventions, coding style, and file layout to improve collaboration and maintenance.
- Standardize patterns for props, hooks, tests, and styling across the repository.
- Keep components small enough that their purpose is obvious from a quick read.

### 9. Build for testability
- Favor pure rendering inputs and clear prop contracts so components are easy to test.
- Isolate side effects in hooks or container layers where possible.
- Avoid hidden dependencies on globals, implicit DOM assumptions, or tightly coupled parent state.

### 10. Choose patterns intentionally
- Use compound components for complex reusable widgets with coordinated child parts.
- Use custom hooks when logic needs to be shared without adding visual wrappers.
- Use container/presentational separation when UI and business logic are both substantial.

## Agent checklist

A coding agent working on React components should be able to:

- Detect when a component has more than one responsibility and split it.
- Extract repeated JSX into reusable components.
- Move business logic into hooks or containers when render files become noisy.
- Recommend a folder location based on whether a component is shared or feature-specific.
- Preserve composition-friendly APIs when refactoring existing components.
- Prevent over-centralized state and unnecessary parent ownership of local UI concerns.

## Practical rules

- One component, one main job.
- One foldering strategy per codebase.
- Shared primitives in shared folders; domain components in feature folders.
- Render logic in components; reusable non-visual logic in hooks.
- Prefer composition, not inheritance-heavy abstractions.
- Refactor when a file becomes hard to scan, test, or reuse.