
# TypeScript & React Course

## TypeScript with React - Essentials

### Defining Components Prop Types

````
export default function CourseGoal({
  title,
  description,
}: {
  title: string;
  description: string;
}) {
  return (
    <article>
      <div>
        <h2>{title}</h2>
        <p>{description}</p>
      </div>
      <button>Delete</button>
    </article>
  );
}
````

Can put it on a type or interface

### Defining a Type for Props with children

````
import { type PropsWithChildren, type ReactNode } from 'react';

// interface CourseGoalProps { // alternative
//   title: string;
//   children: ReactNode
// }

type CourseGoalProps = PropsWithChildren<{ title: string }>;

export default function CourseGoal({ title, children }: CourseGoalProps) {
  return (
    <article>
      <div>
        <h2>{title}</h2>
        {children}
      </div>
      <button>Delete</button>
    </article>
  );
}
````
Can use both aproches
With the key dont need to define props
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzg3OTM4MDU5LDEzOTI2ODA1MTcsNTMxNT
A4MDUxLDEwMjIyNzAyMDksLTE2NDk5NTk5MzksMjEyNzAyMjY2
LDE5OTk4MzkzMzBdfQ==
-->