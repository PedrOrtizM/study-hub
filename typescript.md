
## TypeScript

### Interface

Used to define the **shape of an object**.

```ts
interface User {
  id: number;
  name: string;
}
```

**Pros:**

- Can be extended with extends or by re-declaring the same name.
- Preferred for object structures, especially in OOP and public APIs.

### Types

Used to define any type: primitives, unions, intersections, etc.

```ts
type User = {
  id: number;
  name: string;
};

type Status = 'active' | 'inactive';
type ID = number | string;
```

| Feature                | `interface`         | `type`              |
| ---------------------- | ------------------- | ------------------- |
| Extending              | ✅ Yes               | ✅ Yes               |
| Declaration merging    | ✅ Yes               | ❌ No                |
| Unions & intersections | ❌ No (only extends) | ✅ Yes               |
| Use with primitives    | ❌ No                | ✅ Yes               |
| Recommendation         | Use for objects     | Use for flexibility |

