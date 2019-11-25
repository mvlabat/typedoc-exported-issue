# typedoc-exported-issue
Demonstrates typedoc's inconsistency in excluding not exported symbols

```bash
yarn docs:normal
yarn docs:only-exported
```

Running these two commands generates documentation in `docs/normal` and
`only-exported`.

[src/testDefault1.ts](src/testDefault1.ts):
```typescript
/**
 * Appears in the docs if "Only exported" is checked in the UI,
 * but doesn't if `excludeNotExported` is set to true in `typedocOptions`.
 */
class TestDefault1 {}

export default TestDefault1;
```

[src/testDefault2.ts](src/testDefault2.ts):
```typescript
/**
 * Appears in the docs for both "Only exported" in the UI and
 * `excludeNotExported` set to true in `typedocOptions`.
 */
export default class TestDefault2 {}

```

[src/testDefault1.ts](src/testDefault1.ts):
```typescript
/**
 * Won't appear in the docs as exported.
 */
class TestDefault3 {}

export { TestDefault3 as default };

```
