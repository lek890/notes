### React

Mutations, Subscriptions, timers, logging and other side effects are not allowed inside the main body of a function component (called the render phase). Doing so will lead to confusion and inconsistencies in the UI.

Memoisation is the main performance optimization in react. memo does shallow comparison and if references are the same, rendering is skipped.

Don’t use mutable variables inside render function, use useRef instead.

If what you save in useRef has smaller lifecycle than the component itself, don’t forget to unset the value when disposing the resource.

Memoize functions and objects when needed to improve performance.

Correctly capture input dependencies (undefined => every render, [a, b] => when a or b change, [] => only once).

Use customs hooks for non-trivial use-cases.

Prefer useReducer or functional updates for useState to prevent reading and writing same value in a hook.

Green hooks

- useReducer
- useContext
- useState

Yellow hooks

- useCallback
- useMemo

Red hooks

- useRef
- useEffect
- useLayoutEffect

useMemo is useful for expensive calculations, useCallback is useful for passing callbacks needed for optimized child components.
