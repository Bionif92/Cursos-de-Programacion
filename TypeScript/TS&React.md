
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

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyMjI3MDIwOSwtMTY0OTk1OTkzOSwyMT
I3MDIyNjYsMTk5OTgzOTMzMF19
-->