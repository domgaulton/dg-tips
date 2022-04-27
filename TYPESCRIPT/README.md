# TypeScript

## Typescript Types
* Common types

```ts
export interface StandardTypes {
  name: string;
  age: number;
  developer: boolean;
  interests: InterestsArray[];
}

export interface InterestsArray[] {
  activity: string;
  interested_in: boolean;
}
```

## Export Common Types

* To be used across multiple modules
* Export types as follows;
```ts
export interface StandardTypes {
  name: string;
  age: number;
}
```

* Then import with `type` set
`import type { StandardTypes } from '../../models/StandardTypes';`