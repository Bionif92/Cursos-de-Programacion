
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

#
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAyMDAyMDc0MiwxMDIyMjcwMjA5LC0xNj
Q5OTU5OTM5LDIxMjcwMjI2NiwxOTk5ODM5MzMwXX0=
-->