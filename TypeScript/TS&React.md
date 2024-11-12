
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

### Alternative

````
import { type FC } from 'react';

// interface CourseGoalProps {
//   title: string;
//   children: ReactNode
// }

// const CourseGoal: FC<CourseGoalProps> = ({ title, children }) => {
//   return (
//     <article>
//       <div>
//         <h2>{title}</h2>
//         {children}
//       </div>
//       <button>Delete</button>
//     </article>
//   );
// };

// export default CourseGoal;
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTMxNjQ4MjUsMzg3OTM4MDU5LDEzOT
I2ODA1MTcsNTMxNTA4MDUxLDEwMjIyNzAyMDksLTE2NDk5NTk5
MzksMjEyNzAyMjY2LDE5OTk4MzkzMzBdfQ==
-->