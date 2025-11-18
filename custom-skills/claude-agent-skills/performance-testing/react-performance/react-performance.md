---
name: react-performance
description: React performance optimization specialist. Use PROACTIVELY for identifying and fixing performance bottlenecks, bundle optimization, rendering optimization, and memory leak resolution.
enforcement_level: HIGH
violation_consequence: React applications may have poor performance, memory leaks, or large bundle sizes, leading to slow load times and poor user experience
---

# React Performance Optimization

This skill provides comprehensive guidance for identifying, analyzing, and resolving performance bottlenecks in React applications.

## Overview

React performance optimization involves optimizing rendering, bundle size, memory usage, and Core Web Vitals for React applications. This skill provides systematic approaches to React performance optimization as a React Performance Optimization specialist.

## ✓ Pre-Optimization Checklist

**BEFORE optimizing React performance, verify:**

```yaml
Checklist:
  - [ ] Current performance metrics measured
  - [ ] Performance bottlenecks identified
  - [ ] Bundle size analyzed
  - [ ] Memory usage profiled
  - [ ] Core Web Vitals scores collected
  - [ ] Optimization priorities determined

Status: [READY / BLOCKED]
```

**IF ANY CHECKBOX UNCHECKED:**
- Action: STOP
- Reason: Missing information required for effective React optimization
- Next step: Gather missing information before proceeding

**IF ALL CHECKED:**
- Output: "✅ Pre-optimization verification complete: Ready to optimize React"
- Proceed with: React optimization workflow

## Core Expertise Areas

- **Advanced React Patterns**: Concurrent features, Suspense, error boundaries, context optimization
- **Rendering Performance**: Component re-renders, reconciliation optimization, React.memo, useMemo, useCallback
- **Bundle Optimization**: Code splitting, tree shaking, dynamic imports, Webpack Bundle Analyzer
- **Memory Management**: Memory leaks, cleanup patterns, resource management, efficient state management
- **Network Performance**: Lazy loading, prefetching, caching strategies, resource loading optimization
- **Core Web Vitals**: LCP, FID, CLS optimization specific to React applications
- **Production Monitoring**: Performance profiling, real-time performance tracking
- **Profiling Tools**: React DevTools Profiler, Chrome DevTools, Lighthouse

## When to Use This Skill

Use this skill for:
- Slow loading React applications
- Janky or unresponsive user interactions
- Large bundle sizes affecting load times
- Memory leaks or excessive memory usage
- Poor Core Web Vitals scores
- Performance regression analysis

## Performance Optimization Strategies

### Concurrent React Features
```typescript
// React 18 Concurrent Features
import { startTransition, useDeferredValue, useTransition } from 'react';

function SearchResults({ query }: { query: string }) {
  const [isPending, startTransition] = useTransition();
  const [results, setResults] = useState([]);
  const deferredQuery = useDeferredValue(query);

  // Heavy search operation with transition
  const searchHandler = (newQuery: string) => {
    startTransition(() => {
      // This won't block the UI
      setResults(performExpensiveSearch(newQuery));
    });
  };

  return (
    <div>
      <SearchInput onChange={searchHandler} />
      {isPending && <SearchSpinner />}
      <ResultsList results={results} query={deferredQuery} />
    </div>
  );
}
```

### Advanced Memoization Strategies
```typescript
// Deep comparison memoization
import { memo, useMemo } from 'react';

const ExpensiveComponent = memo(({ data, config }) => {
  // Memoize expensive computations
  const processedData = useMemo(() => {
    return data
      .filter(item => item.active)
      .map(item => processComplexCalculation(item, config))
      .sort((a, b) => b.priority - a.priority);
  }, [data, config]);

  return <Chart data={processedData} />;
}, (prevProps, nextProps) => {
  // Custom comparison function for complex objects
  return isEqual(prevProps.data, nextProps.data) && 
         isEqual(prevProps.config, nextProps.config);
});
```

### Virtualization for Large Lists
```typescript
// React Window for performance
import { FixedSizeList as List } from 'react-window';

const VirtualizedList = ({ items }: { items: any[] }) => {
  const Row = ({ index, style }: { index: number; style: any }) => (
    <div style={style}>
      <ItemComponent item={items[index]} />
    </div>
  );

  return (
    <List height={400} itemCount={items.length} itemSize={50} width="100%">
      {Row}
    </List>
  );
};
```

### Advanced Code Splitting
```typescript
// Route-based splitting with preloading
import { lazy, Suspense } from 'react';

const Dashboard = lazy(() => 
  import('./Dashboard').then(module => ({ default: module.Dashboard }))
);

const Analytics = lazy(() => 
  import(/* webpackChunkName: "analytics" */ './Analytics')
);

// Preload critical routes
const preloadRoute = (routeName: string) => {
  const route = routeMap[routeName];
  route.component.preload();
};
```

### React.memo for Component Memoization
- Use React.memo for expensive components
- Implement useMemo for expensive computations
- Use useCallback for stable function references
- Custom comparison functions for complex props

### Code Splitting with React.lazy
- Lazy load routes and components
- Use Suspense for loading states
- Implement progressive loading
- Preload critical routes

### Bundle Optimization
- Code splitting and dynamic imports
- Tree shaking unused code
- Optimize dependencies
- Use production builds
- Webpack Bundle Analyzer for analysis

## Best Practices

- Profile before optimizing
- Focus on biggest bottlenecks first
- Use React DevTools Profiler
- Monitor Core Web Vitals
- Test performance improvements

## Tools and Methods

- **Read**: Analyze React code, bundle analysis, and performance profiles
- **Write/Edit**: Optimize React components, implement code splitting, fix memory leaks
- **Bash**: Run build tools, analyze bundles, profile performance

