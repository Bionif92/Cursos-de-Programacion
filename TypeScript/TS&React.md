
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

### UseState and TS

````
import { useState } from 'react';

import CourseGoal from './components/CourseGoal.tsx';
import Header from './components/Header.tsx';
import goalsImg from './assets/goals.jpg';

type CourseGoal = {
  title: string;
  description: string;
  id: number;
};

export default function App() {
  --const [goals, setGoals] = useState<CourseGoal[]>([]);

  function handleAddGoal() {
    setGoals((prevGoals) => {
      --const newGoal: CourseGoal = {
        id: Math.random(),
        title: 'Learn React + TS',
        description: 'Learn it in depth!',
      };
      return [...prevGoals, newGoal];
    });
  }

  return (
    <main>
      <Header image={{ src: goalsImg, alt: 'A list of goals' }}>
        <h1>Your Course Goals</h1>
      </Header>
      <button onClick={handleAddGoal}>Add Goal</button>
      <ul>
        {goals.map((goal) => (
          <li key={goal.id}>
            <CourseGoal title={goal.title}>
              <p>{goal.description}</p>
            </CourseGoal>
          </li>
        ))}
      </ul>
    </main>
  );
}
````

### Passing Functions as Values in a TS way

````
import CourseGoal from './CourseGoal.tsx';
import { type CourseGoal as CGoal } from '../App.tsx';

type CourseGoalListProps = {
  goals: CGoal[];
  onDeleteGoal: (id: number) => void;
};

export default function CourseGoalList({
  goals,
  onDeleteGoal,
}: CourseGoalListProps) {
  return (
    <ul>
      {goals.map((goal) => (
        <li key={goal.id}>
          <CourseGoal id={goal.id} title={goal.title} onDelete={onDeleteGoal}>
            <p>{goal.description}</p>
          </CourseGoal>
        </li>
      ))}
    </ul>
  );
}
````

### Handling & Typing Events

````
import { type FormEvent } from 'react';

export default function NewGoal() {
  --function handleSubmit(event: FormEvent) {
    event.preventDefault();
  }

  return (
    <form onSubmit={handleSubmit}>
      <p>
        <label htmlFor="goal">Your goal</label>
        <input id="goal" type="text" />
      </p>
      <p>
        <label htmlFor="summary">Short summary</label>
        <input id="summary" type="text" />
      </p>
      <p>
        <button>Add Goal</button>
      </p>
    </form>
  );
}
````

### Ref() with TS

````
import { useRef, type FormEvent } from 'react';

type NewGoalProps = {
  onAddGoal: (goal: string, summary: string) => void;
};

export default function NewGoal({ onAddGoal }: NewGoalProps) {
  -- const goal = useRef<HTMLInputElement>(null); // need to start with null not to have error
 -- const summary = useRef<HTMLInputElement>(null);

  function handleSubmit(event: FormEvent<HTMLFormElement>) {
    event.preventDefault();

    const enteredGoal = goal.current!.value; // ! you know it wont be null
    const enteredSummary = summary.current!.value;

    event.currentTarget.reset();
    onAddGoal(enteredGoal, enteredSummary);
  }

  return (
    <form onSubmit={handleSubmit}>
      <p>
        <label htmlFor="goal">Your goal</label>
        <input id="goal" type="text" ref={goal} />
      </p>
      <p>
        <label htmlFor="summary">Short summary</label>
        <input id="summary" type="text" ref={summary} />
      </p>
      <p>
        <button>Add Goal</button>
      </p>
    </form>
  );
}
````

## Advanced Component Types - Dynamic Components, Polymorphic Components & More

### Dynamic & Flexible Component

Adding a React Node dynamically
````
import { type ReactNode } from 'react';

import CourseGoal from './CourseGoal.tsx';
import { type CourseGoal as CGoal } from '../App.tsx';
import InfoBox from './InfoBox.tsx';

type CourseGoalListProps = {
  goals: CGoal[];
  onDeleteGoal: (id: number) => void;
};

export default function CourseGoalList({
  goals,
  onDeleteGoal,
}: CourseGoalListProps) {
  if (goals.length === 0) {
    return (
      <InfoBox mode="hint">
        You have no course goals yet. Start adding some!
      </InfoBox>
    );
  }

--  let warningBox: ReactNode; // adding jsx code

--  if (goals.length >= 4) {
    warningBox = (
      <InfoBox mode="warning">
        You're collecting a lot of goals. Don't put too much on your plate!
      </InfoBox>
    );
  }

  return (
    <>
      {warningBox}
      <ul>
        {goals.map((goal) => (
          <li key={goal.id}>
            <CourseGoal id={goal.id} title={goal.title} onDelete={onDeleteGoal}>
              <p>{goal.description}</p>
            </CourseGoal>
          </li>
        ))}
      </ul>
    </>
  );
}
````

### Flexible Components with required prop combinations

Use Discriminated Unions to generate two types of props entries
````
import { type ReactNode } from 'react';

type HintBoxProps = {
  mode: 'hint';
  children: ReactNode;
};

type WarningBoxProps = {
  mode: 'warning';
  severity: 'low' | 'medium' | 'high';
  children: ReactNode;
};

type InfoBoxProps = HintBoxProps | WarningBoxProps;

export default function InfoBox(props: InfoBoxProps) {
  const { children, mode } = props;

  if (mode === 'hint') {
    return (
      <aside className="infobox infobox-hint">
        <p>{children}</p>
      </aside>
    );
  }

  const { severity } = props;

  return (
    <aside className={`infobox infobox-warning warning--${severity}`}>
      <h2>Warning</h2>
      <p>{children}</p>
    </aside>
  );
}
````

### Wrapper component with ComponentPropsWithoutRefs

Spreading the props
````
import { ComponentPropsWithoutRef } from 'react';

type InputProps = {
  label: string;
  id: string;
} & ComponentPropsWithoutRef<'input'>; // all the ..props for an input

export default function Input({label, id, ...props}: InputProps) {
  return (
    <p>
      <label htmlFor={id}>{label}</label>
      <input id={id} {...props} />
    </p>
  );
}
````

### Wrapper component render different elements

````
import { type ComponentPropsWithoutRef } from 'react';

type ButtonProps = {
  el: 'button';
} & ComponentPropsWithoutRef<'button'>;

type AnchorProps = {
  el: 'anchor';
} & ComponentPropsWithoutRef<'a'>;

export default function Button(props: ButtonProps | AnchorProps) {
  // const {el, ...otherProps} = props;
  if (props.el === 'anchor') {
    return <a className="button" {...props}></a>;
  }

  return <button className="button" {...props}></button>;
}
````

### Type Predicates & Facing TS Limitations

Eliminate the prop for choosing an a or button, see if it has the prop to render conditionally

````
import { type ComponentPropsWithoutRef } from 'react';

type ButtonProps = ComponentPropsWithoutRef<'button'> & {
  href?: never;
};

type AnchorProps = ComponentPropsWithoutRef<'a'> & {
  href?: string;
};

--function isAnchorProps(props: ButtonProps | AnchorProps): props is AnchorProps {
  return 'href' in props; // type, is a boolean, if it is true, the prop is AnchorProps
}

export default function Button(props: ButtonProps | AnchorProps) {
  if (isAnchorProps(props)) {
    return <a className="button" {...props}></a>;
  }

  return <button className="button" {...props}></button>;
}
````

### Polimorphic Component

Render a component with nested components

````
import { type ElementType } from 'react';

type ContainerProps = {
  as: ElementType
};

export default function Container({as}: ContainerProps) {
  const Component = as; // need an uppercase element in the component
  return <Component />
}
````

### Polimorphic Component with Generics

Add props of the concrete component
````
import {
  type ReactNode,
  type ElementType,
  type ComponentPropsWithoutRef,
} from 'react';

type ContainerProps<T extends ElementType> = {
  as?: T;
  children: ReactNode;
} & ComponentPropsWithoutRef<T>;

export default function Container<C extends ElementType>({
  as,
  children,
  ...props
}: ContainerProps<C>) {
  const Component = as || 'div';
  return (
    <Component {...props}>
      {children}
    </Component>
  );
}
````

### Using forwardRef with TS

````
//Input.tsx
import { forwardRef, type ComponentPropsWithoutRef } from 'react';

type InputProps = {
  label: string;
  id: string;
} & ComponentPropsWithoutRef<'input'>;

const Input = forwardRef<HTMLInputElement // linked to the type of ref, InputProps>(function Input(
  { label, id, ...props },
  ref
) {
  return (
    <p>
      <label htmlFor={id}>{label}</label>
      <input id={id} {...props} ref={ref} />
    </p>
  );
});

export default Input;
````
````
//App.tsx
import { useRef } from 'react';

import Input from './components/Input.tsx';

function App() {
  const input = useRef<HTMLInputElement>(null);

  return (
    <main>
      <Input label="Test" id="test" ref={input} />
    </main>
  );
}

export default App;
````

### Wrapper Component, unknown type and as to modify type

````
//form.tsx
import { type FormEvent, type ComponentPropsWithoutRef } from 'react';

type FormProps = ComponentPropsWithoutRef<'form'> & {
  onSave: (value: unknown) => void; // use unknown type
};

export default function Form({ onSave, children, ...otherProps }: FormProps) {
  function handleSubmit(event: FormEvent<HTMLFormElement>) {
    event.preventDefault();

    const formData = new FormData(event.currentTarget);
    const data = Object.fromEntries(formData);
    onSave(data);
  }

  return (
    <form onSubmit={handleSubmit} {...otherProps}>
      {children}
    </form>
  );
}
````
````
//app.tsx
import { useRef } from 'react';

import Input from './components/Input.tsx';
import Form from './components/Form.tsx';
import Button from './components/Button.tsx';

function App() {
  function handleSave(data: unknown) {
    --const extractedData = data as { name: string; age: string }; // as to convert the type
    console.log(extractedData);
  }

  return (
    <main>
      <Form onSave={handleSave}>
        <Input type="text" label="Name" id="name" />
        <Input type="number" label="Age" id="age" />
        <p>
          <Button>Save</Button>
        </p>
      </Form>
    </main>
  );
}

export default App;
````

### Exposing component API with useImperativeHandle

Expose some callable function

Need to be wrapped in a fowardedref to use it

````
//form.tsx
import {
  type FormEvent,
  type ComponentPropsWithoutRef,
  useRef,
  useImperativeHandle,
  forwardRef,
} from 'react';

--export type FormHandle = {
  clear: () => void;
};

type FormProps = ComponentPropsWithoutRef<'form'> & {
  onSave: (value: unknown) => void;
};

const Form = forwardRef<FormHandle// for the ref, FormProps>(function Form(
  { onSave, children, ...otherProps },
  ref
) {
  const form = useRef<HTMLFormElement>(null);

  --useImperativeHandle(ref, () => {
    return {
      clear() {
        console.log('CLEARING');
        form.current?.reset();
      },
    };
  });

  function handleSubmit(event: FormEvent<HTMLFormElement>) {
    event.preventDefault();

    const formData = new FormData(event.currentTarget);
    const data = Object.fromEntries(formData);
    onSave(data);
  }

  return (
    <form onSubmit={handleSubmit} {...otherProps} ref={form}>
      {children}
    </form>
  );
});

export default Form;
````
````
//app.tsx
import { useRef } from 'react';

import Input from './components/Input.tsx';
import Form, { type FormHandle } from './components/Form.tsx';
import Button from './components/Button.tsx';

function App() {
  --const customForm = useRef<FormHandle>(null);

  function handleSave(data: unknown) {
    const extractedData = data as { name: string; age: string };
    console.log(extractedData);
    --customForm.current?.clear();
  }

  return (
    <main>
      --<Form onSave={handleSave} ref={customForm}>
        <Input type="text" label="Name" id="name" />
        <Input type="number" label="Age" id="age" />
        <p>
          <Button>Save</Button>
        </p>
      </Form>
    </main>
  );
}

export default App;
````

### Avoid Type Casting with as

In the previous lecture, we used  _"Type Casting"_ (also called  _"Type Assertion"_) via TypeScript's  `as`  keyword to  _"tell"_  TypeScript that a value is of a specific type.

This is a technique that makes sense when working with data where TypeScript has no chance of inferring the type where you on the other hand no the exact type.

If you're not 100% sure about the type of value you'll be dealing with at runtime (i.e., if there are multiple possible value types) or if you want to be extra safe, you can also use a combination of  _"Type Guards"_  to narrow down the type until TypeScript is able to infer the final type.

Here's the code from the previous lecture, now adjusted to use  _"Type Guards"_  for  _"Type Narrowing"_:

````
function handleSave(data: unknown) {
  // const extractedData = data as { name: string; age: string };
  if (
    !data ||
    typeof data !== 'object' ||
    !('name' in data) ||
    !('age' in data)
  ) {
      return;
  }

  // at this point, TypeScript knows that data MUST BE an object 
  // with a name and age property
  // otherwise, the previous if statement would have returned
  console.log(data);
  customForm.current?.clear();
}
````

## Advanced Type-Safe State with Context API & useReducer()

### Creating a Context & Fitting Types

````
````

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzUwMjY1OTMxLDE3NTgzNDg4MSw5Nzg1NT
MxOTMsLTIwNDAyMjA2MzIsOTk0NTc2NTMzLC0xODczODUyMjg0
LC0xNDczMDg4NzcyLC0xNzI2NTIxMjQ4LDE1Mzg5Nzc2NjQsLT
E4NzIxMTA0ODQsMzQ1MTYxODYyLDgxNzI2NDA3Nyw1NzE3OTUw
MDMsMTQzNDk1NjYzLC0xMzkxNjM1MDMwLDMwNTkyMjQwMiwtMj
EwMzMyNzA5OSwtMjY5NzE5OTQ2LDM5MjQ4NDMzOCwxMjk0ODQ1
OTYxXX0=
-->