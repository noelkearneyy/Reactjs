# useCallback Hook
- useCallback returns a memoised callback. Pass an inline callback and an array of dependencies. useCallback will return a memoized version of the callback that only changes if one of the dependencies has changed. 
- Useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders. 

```
useCallback(fn, dependancies) === useMemo(()=> fn, dependancies)
```
- 

## Sources
- https://reactjs.org/docs/hooks-reference.html
- https://www.youtube.com/watch?v=_AyFP5s69N4
