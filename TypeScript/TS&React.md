
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


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NTg5MDU2NzYsMTUzODk3NzY2NCwtMT
g3MjExMDQ4NCwzNDUxNjE4NjIsODE3MjY0MDc3LDU3MTc5NTAw
MywxNDM0OTU2NjMsLTEzOTE2MzUwMzAsMzA1OTIyNDAyLC0yMT
AzMzI3MDk5LC0yNjk3MTk5NDYsMzkyNDg0MzM4LDEyOTQ4NDU5
NjEsODA0Njk2ODI3LC0xMTM4MzMxNzkyLC04NzE1ODgyNjgsLT
k1OTM4NDI2MSwtMjA4MDQ0NzkzMywxMTEzMTM4MDYwLC0xNDY0
MTE0MDc5XX0=
-->