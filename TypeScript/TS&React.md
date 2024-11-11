
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTMxNTA4MDUxLDEwMjIyNzAyMDksLTE2ND
k5NTk5MzksMjEyNzAyMjY2LDE5OTk4MzkzMzBdfQ==
-->