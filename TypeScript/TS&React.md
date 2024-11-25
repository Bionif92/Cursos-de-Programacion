
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

### Creating a Context & Provider Component

````
import { type ReactNode, createContext, useContext } from 'react';

type Timer = {
  name: string;
  duration: number;
};

type TimersState = {
  isRunning: boolean;
  timers: Timer[];
};

type TimersContextValue = TimersState & {
  addTimer: (timerData: Timer) => void;
  startTimers: () => void;
  stopTimers: () => void;
};

const TimersContext = createContext<TimersContextValue | null>(null);

export function useTimersContext() {
  const timersCtx = useContext(TimersContext)

  if (timersCtx === null) {
    throw new Error('TimersContext is null - that should not be the case!');
  }

  return timersCtx;
}

type TimersContextProviderProps = {
  children: ReactNode;
};

export default function TimersContextProvider({ children }: TimersContextProviderProps) {
  const ctx: TimersContextValue = {
    timers: [],
    isRunning: true,
    addTimer(timerData) {
      // ...
    },
    startTimers() {
      // ...
    },
    stopTimers() {
      // ...
    },
  };
  return (
    <TimersContext.Provider value={ctx}>{children}</TimersContext.Provider>
  );
}
````
Wrap component with provider:
````
//app.tsx
import AddTimer from './components/AddTimer.tsx';
import Header from './components/Header.tsx';
import Timers from './components/Timers.tsx';
import TimersContextProvider from './store/timers-context.tsx';

function App() {
  return (
    <TimersContextProvider>
      <Header />
      <main>
        <AddTimer />
        <Timers />
      </main>
    </TimersContextProvider>
  );
}

export default App;
````

### Accesing Context with Custom Hook

 useTimersContext is the hook
````
//context
import { type ReactNode, createContext, useContext } from 'react';

export function useTimersContext() {
  const timersCtx = useContext(TimersContext)

  if (timersCtx === null) {
    throw new Error('TimersContext is null - that should not be the case!');
  }

  return timersCtx;
}
````
````
//header.tsx
import Button from './UI/Button.tsx';
import { useTimersContext } from '../store/timers-context.tsx';

export default function Header() {
  const timersCtx = useTimersContext();

  return (
    <header>
      <h1>ReactTimer</h1>

      <Button>{timersCtx.isRunning ? 'Stop' : 'Start'} Timers</Button>
    </header>
  );
}
````

### useReducer

````
//context
import { type ReactNode, createContext, useContext, useReducer } from 'react';

type Timer = {
  name: string;
  duration: number;
};

type TimersState = {
  isRunning: boolean;
  timers: Timer[];
};

--const initialState: TimersState = {
  isRunning: true,
  timers: [],
};

type TimersContextValue = TimersState & {
  addTimer: (timerData: Timer) => void;
  startTimers: () => void;
  stopTimers: () => void;
};

const TimersContext = createContext<TimersContextValue | null>(null);

export function useTimersContext() {
  const timersCtx = useContext(TimersContext);

  if (timersCtx === null) {
    throw new Error('TimersContext is null - that should not be the case!');
  }

  return timersCtx;
}

type TimersContextProviderProps = {
  children: ReactNode;
};

type StartTimersAction = {
  type: 'START_TIMERS';
};

type StopTimersAction = {
  type: 'STOP_TIMERS';
};

type AddTimerAction = {
  type: 'ADD_TIMER';
  payload: Timer;
};

type Action = StartTimersAction | StopTimersAction | AddTimerAction;

function timersReducer(state: TimersState, action: Action): TimersState {
  if (action.type === 'START_TIMERS') {
    // state.isRunning = true;
    return {
      ...state,
      isRunning: true,
    };
  }
  if (action.type === 'STOP_TIMERS') {
    return {
      ...state,
      isRunning: false,
    };
  }
  if (action.type === 'ADD_TIMER') {
    return {
      ...state,
      timers: [
        ...state.timers,
        {
          name: action.payload.name,
          duration: action.payload.duration,
        },
      ],
    };
  }

  return state;
}

export default function TimersContextProvider({
  children,
}: TimersContextProviderProps) {
  --const [timersState, dispatch] = useReducer(timersReducer, initialState);

  const ctx: TimersContextValue = {
    timers: timersState.timers,
    isRunning: timersState.isRunning,
    addTimer(timerData) {
      dispatch({ type: 'ADD_TIMER', payload: timerData });
    },
    startTimers() {
      dispatch({ type: 'START_TIMERS' });
    },
    stopTimers() {
      dispatch({ type: 'STOP_TIMERS' });
    },
  };
  return (
    <TimersContext.Provider value={ctx}>{children}</TimersContext.Provider>
  );
}
````

### Finishing the app

````
//header.tsx
import Button from './UI/Button.tsx';
import { useTimersContext } from '../store/timers-context.tsx';

export default function Header() {
  const timersCtx = useTimersContext();

  return (
    <header>
      <h1>ReactTimer</h1>

      <Button
        onClick={
          timersCtx.isRunning ? timersCtx.stopTimers : timersCtx.startTimers
        }
      >
        {timersCtx.isRunning ? 'Stop' : 'Start'} Timers
      </Button>
    </header>
  );
}
````
````
//addtimer.tsx
import { useRef } from 'react';

import Button from './UI/Button.tsx';
import Form, { FormHandle } from './UI/Form.tsx';
import Input from './UI/Input.tsx';
import { useTimersContext } from '../store/timers-context.tsx';

export default function AddTimer() {
  const form = useRef<FormHandle>(null);
 -- const { addTimer } = useTimersContext();

  function handleSaveTimer(data: unknown) {
    const extractedData = data as { name: string; duration: string };
   -- addTimer({ name: extractedData.name, duration: +extractedData.duration });
    form.current?.clear();
  }

  return (
    <Form ref={form} onSave={handleSaveTimer} id="add-timer">
      <Input type="text" label="Name" id="name" />
      <Input type="number" label="Duration" id="duration" />
      <p>
        <Button>Add Timer</Button>
      </p>
    </Form>
  );
}
````
````
//timer.tsx
import Container from './UI/Container.tsx';
import { type Timer as TimerProps } from '../store/timers-context.tsx';

export default function Timer({ name, duration }: TimerProps) {
  return (
    <Container as="article">
      <h2>{name}</h2>
      <p>{duration}</p>
    </Container>
  );
}
````
````
//timers.tsx
import { useTimersContext } from '../store/timers-context.tsx';
import Timer from './Timer.tsx';

export default function Timers() {
  const { timers } = useTimersContext();
  return (
    <ul>
      {timers.map((timer) => (
        <li key={timer.name}>
          <Timer {...timer} />
        </li>
      ))}
    </ul>
  );
}
````

## Side Effects, useEffect() & Data Fetching with TypeScript

### Side Effect, ref

No difference with TS

Use ref to have the reference of the timer and clear it

````
import { useEffect, useRef, useState } from 'react';

import Container from './UI/Container.tsx';
import { type Timer as TimerProps } from '../store/timers-context.tsx';

export default function Timer({ name, duration }: TimerProps) {
  const interval = useRef<number | null>(null);
  const [remainingTime, setRemainingTime] = useState(duration * 1000);

  if (remainingTime <= 0 && interval.current) {
    clearInterval(interval.current);
  }

  useEffect(() => {
    const timer = setInterval(function () { // need a local variable 
      setRemainingTime((prevTime) => 
      if (prevTime <= 0) {
    return prevTime;
  }
  return prevTime - 50;
    }, 50);
    interval.current = timer;

    return () => clearInterval(timer);
  }, []);

  const formattedRemainingTime = (remainingTime / 1000).toFixed(2);

  return (
    <Container as="article">
      <h2>{name}</h2>
      <p>
        <progress max={duration * 1000} value={remainingTime} />
      </p>
      <p>{formattedRemainingTime}</p>
    </Container>
  );
}
````

### useEffect & Its Deppendencies

Stop the timers
````
import { useEffect, useRef, useState } from 'react';

import Container from './UI/Container.tsx';
import { useTimersContext, type Timer as TimerProps } from '../store/timers-context.tsx';

export default function Timer({ name, duration }: TimerProps) {
  const interval = useRef<number | null>(null);
  const [remainingTime, setRemainingTime] = useState(duration * 1000);
 -- const { isRunning } = useTimersContext();

  if (remainingTime <= 0 && interval.current) {
    clearInterval(interval.current);
  }

 -- useEffect(() => {
    let timer: number;
    
    if (isRunning) {
      timer = setInterval(function () {
        setRemainingTime((prevTime) => prevTime - 50);
      }, 50);
      interval.current = timer;

    } else if (interval.current) {
      clearInterval(interval.current)
    }

    return () => clearInterval(timer);
  }, [isRunning]);

  const formattedRemainingTime = (remainingTime / 1000).toFixed(2);

  return (
    <Container as="article">
      <h2>{name}</h2>
      <p>
        <progress max={duration * 1000} value={remainingTime} />
      </p>
      <p>{formattedRemainingTime}</p>
    </Container>
  );
}
````

### Data Fetching, get Utility function with TS

````
//util/htpp.ts
export async function get(url: string) {
  const response = await fetch(url);

  if (!response.ok) {
    throw new Error('Failed to fetch data.');
  }

  const data = await response.json() as unknown; // more type security than with any
  return data;
}
````

### Fetching and transforming data

````
import { type ReactNode, useEffect, useState } from 'react';

import BlogPosts, { BlogPost } from './components/BlogPosts.tsx';
import { get } from './util/http.ts';
import fetchingImg from './assets/data-fetching.png';

type RawDataBlogPost = {
  id: number;
  userId: number;
  title: string;
  body: string;
};

function App() {
  const [fetchedPosts, setFetchedPosts] = useState<BlogPost[]>();

  useEffect(() => {
    async function fetchPosts() {
      const data = (await get(
        'https://jsonplaceholder.typicode.com/posts'
      )) as RawDataBlogPost[];

//convert data into the data needed in the state
      const blogPosts: BlogPost[] = data.map((rawPost) => {
        return {
          id: rawPost.id,
          title: rawPost.title,
          text: rawPost.body,
        };
      });

      setFetchedPosts(blogPosts);
    }

    fetchPosts();
  }, []);

  let content: ReactNode;

  if (fetchedPosts) { // because can be undefined
    content = <BlogPosts posts={fetchedPosts} />;
  }

  return (
    <main>
      <img
        src={fetchingImg}
        alt="An abstract image depicting a data fetching process."
      />
      {content}
    </main>
  );
}

export default App;
````

### Using Zod Library for Response Data Validation

When fetching data, it can be a good idea to parse & validate the fetched data to check if it's in line with your data structure expectations.

A great library for doing that validation is the  [Zod](https://zod.dev/)  library because this library embraces TypeScript and is written such that TypeScript is able to infer the structure of the parsed / validated data.

I could create an entire course about Zod, but here's a very brief introduction.

When working with Zod (after installing it via  `npm install zod`), your main task is to create a schema for the data you're trying to validate.

For example, when fetching blog posts, you would define the schema for a single blog post:

````
import { z } from 'zod';

const rawDataBlogPostSchema = z.object({
  id: z.number(),
  userId: z.number(),
  title: z.string(),
  body: z.string(),
});
````

**Important:** This is JavaScript code! It will be compiled and will execute at runtime.

But, under the hood, it's written such that, during development, TypeScript is able to infer the type of the values that will be parsed / validated via that schema.

Speaking of that, here's how you would use this  `rawDataBlogPostSchema`  to validate a value:

````
const parsedData = rawDataBlogPostSchema.parse(someData)
````

This will throw an error if  `someData`  is not in line with the defined schema (e.g., if a property is missing or of a different value type).

It will return the parsed data if validation succeeds.

The great thing is, that TypeScript now knows the type of  `parsedData`  => It will be the type you set up in your schema.

In this example, TypeScript would know that  `parsedData`  contains the properties  `id`  (number),  `userId`  (number),  `title`  (string) and  `body`  (string).

Therefore, even if  `someData`  was  `any`  or  `unknown`,  `parsedData`  will be a known type.

When using Zod in the course demo app, you could therefore adjust the  `App`  component file like this:

````
import { z } from 'zod';
// other imports ...

// outside of App component function (since this doesn't need to be re-created all the time)
const rawDataBlogPostSchema = z.object({
  id: z.number(),
  userId: z.number(),
  title: z.string(),
  body: z.string(),
});
// z.array() is a Zod method that creates a new schema based on another schema
// as the name suggests, it's simply an array containing the expected objects
const expectedResponseDataSchema = z.array(rawDataBlogPostSchema);

function App() {
  // other code like useState() etc ...

  useEffect(() => {
    async function fetchPosts() {
      setIsFetching(true);
      try {
        const data = await get(
          'https://jsonplaceholder.typicode.com/posts'
        );
        const parsedData = expectedResponseDataSchema.parse(data);
        // No more type casting via "as" needed!
        // Instead, here, TypeScript "knows" that parsedData will be an array
        // full with objects as defined by the above schema
        const blogPosts: BlogPost[] = parsedData.map((rawPost) => {
          return {
            id: rawPost.id,
            title: rawPost.title,
            text: rawPost.body,
          };
        });
        setFetchedPosts(blogPosts);
      } catch (error) {
        if (error instanceof Error) {
          setError(error.message);
        }
        // setError('Failed to fetch posts!');
      }

      setIsFetching(false);
    }

    fetchPosts();
  }, []);

  // other code ...
}
````

### Alternative Generic Function

As always, there are, of course, multiple ways of building the  `get`  function.

You could, for example, also build it as a generic function that accepts the expected return value type as a type argument:

````
export async function get<T>(url: string) {
  const response = await fetch(url);

  if (!response.ok) {
    throw new Error('Failed to fetch data.');
  }

  const data = await response.json() as unknown; 
  return data as T;
}
````
````
const data = await get<RawDataBlogPost[]>(
  'https://jsonplaceholder.typicode.com/posts'
);
````

### Handling Errors & Loading States

````
import { type ReactNode, useEffect, useState } from 'react';

import BlogPosts, { BlogPost } from './components/BlogPosts.tsx';
import { get } from './util/http.ts';
import fetchingImg from './assets/data-fetching.png';
import ErrorMessage from './components/ErrorMessage.tsx';

type RawDataBlogPost = {
  id: number;
  userId: number;
  title: string;
  body: string;
};

function App() {
  const [fetchedPosts, setFetchedPosts] = useState<BlogPost[]>();
  const [isFetching, setIsFetching] = useState(false);
  const [error, setError] = useState<string>();

  useEffect(() => {
    async function fetchPosts() {
      setIsFetching(true);
      try {
        const data = (await get(
          'https://jsonplaceholder.typicode.com/posts'
        )) as RawDataBlogPost[];
        const blogPosts: BlogPost[] = data.map((rawPost) => {
          return {
            id: rawPost.id,
            title: rawPost.title,
            text: rawPost.body,
          };
        });
        setFetchedPosts(blogPosts);
      } catch (error) {
        if (error instanceof Error) { // see if it is the object error
          setError(error.message);
        }
        // setError('Failed to fetch posts!');
      }

      setIsFetching(false);
    }

    fetchPosts();
  }, []);

  let content: ReactNode;

  if (error) {
    content = <ErrorMessage text={error} />;
  }

  if (fetchedPosts) {
    content = <BlogPosts posts={fetchedPosts} />;
  }

  if (isFetching) {
    content = <p id="loading-fallback">Fetching posts...</p>;
  }

  return (
    <main>
      <img
        src={fetchingImg}
        alt="An abstract image depicting a data fetching process."
      />
      {content}
    </main>
  );
}

export default App;
````

## Using Redux with TypeScript

### Redux Store & First Slice

````
//store/store.ts
import { configureStore } from '@reduxjs/toolkit';

import { cartSlice } from './cart-slice.ts';

configureStore({
  reducer: {
    cart: cartSlice.reducer
  }
});
````
````
//store/cart-slice.ts
import { createSlice } from '@reduxjs/toolkit';

type CartItem = {
  id: string;
  title: string;
  price: number;
  quantity: number;
};

type CartState = {
  items: CartItem[]
};

const initialState: CartState = {
  items: []
}

export const cartSlice = createSlice({
  name: 'cart',
  initialState,
  reducers: {
    addToCart() {},
    removeFromCart() {}
  }
});
````

### First Reducer & Controling the action payload Type

Can mutate the state in redux not with useReducer
````
//store/cart-slice.ts
-- import { createSlice, type PayloadAction } from '@reduxjs/toolkit';

type CartItem = {
  id: string;
  title: string;
  price: number;
  quantity: number;
};

type CartState = {
  items: CartItem[];
};

const initialState: CartState = {
  items: [],
};

export const cartSlice = createSlice({
  name: 'cart',
  initialState,
  reducers: {
    addToCart(
      state,
    --action: PayloadAction<{ id: string; title: string; price: number }>
    ) {
      const itemIndex = state.items.findIndex(
        (item) => item.id === action.payload.id
      );

      if (itemIndex >= 0) {
        state.items[itemIndex].quantity++;
      } else {
        state.items.push({ ...action.payload, quantity: 1 });
      }
    },
    removeFromCart(state, action: PayloadAction<string>) {
      const itemIndex = state.items.findIndex(
        (item) => item.id === action.payload
      );

      if (state.items[itemIndex].quantity === 1) {
        state.items.splice(itemIndex, 1);
      } else {
        state.items[itemIndex].quantity--;
      }
    },
  },
});
````

### Providing the Redux Store

````
//store/store.ts
import { configureStore } from '@reduxjs/toolkit';

import { cartSlice } from './cart-slice.ts';

export const store = configureStore({
  reducer: {
    cart: cartSlice.reducer
  }
});

export type AppDispatch = typeof store.dispatch;
````
````
//app.tsx
--import { Provider } from 'react-redux';

import Header from './components/Header.tsx';
import Shop from './components/Shop.tsx';
import Product from './components/Product.tsx';
import { DUMMY_PRODUCTS } from './dummy-products.ts';
import { store } from './store/store.ts';

function App() {
  return (
    --<Provider store={store}>
      <Header />
      <Shop>
        {DUMMY_PRODUCTS.map((product) => (
          <li key={product.id}>
            <Product {...product} />
          </li>
        ))}
      </Shop>
    </Provider>
  );
}

export default App;
````

### Dispatching Actions & Adjusting the useDispatch Hook

Export the actions
````
import { createSlice, type PayloadAction } from '@reduxjs/toolkit';

type CartItem = {
  id: string;
  title: string;
  price: number;
  quantity: number;
};

type CartState = {
  items: CartItem[];
};

const initialState: CartState = {
  items: [],
};

export const cartSlice = createSlice({
  name: 'cart',
  initialState,
  reducers: {
    addToCart(
      state,
      action: PayloadAction<{ id: string; title: string; price: number }>
    ) {
      const itemIndex = state.items.findIndex(
        (item) => item.id === action.payload.id
      );

      if (itemIndex >= 0) {
        state.items[itemIndex].quantity++;
      } else {
        state.items.push({ ...action.payload, quantity: 1 });
      }
    },
    removeFromCart(state, action: PayloadAction<string>) {
      const itemIndex = state.items.findIndex(
        (item) => item.id === action.payload
      );

      if (state.items[itemIndex].quantity === 1) {
        state.items.splice(itemIndex, 1);
      } else {
        state.items[itemIndex].quantity--;
      }
    },
  },
});

--export const { addToCart, removeFromCart } = cartSlice.actions;
````

For extra type safety, create your file with useDispatch

````
/store/store.ts
import { configureStore } from '@reduxjs/toolkit';

import { cartSlice } from './cart-slice.ts';

export const store = configureStore({
  reducer: {
    cart: cartSlice.reducer
  }
});

--export type AppDispatch = typeof store.dispatch; // type of dispatch
````

````
/store/hooks.ts
import { useDispatch } from 'react-redux';

import { AppDispatch } from './store.ts';

type DispatchFunction = () => AppDispatch;

export const useCartDispatch: DispatchFunction = useDispatch;
````

Use the actions

````
/product.tsx
import { addToCart } from '../store/cart-slice.ts';
import { useCartDispatch } from '../store/hooks.ts';

type ProductProps = {
  id: string;
  image: string;
  title: string;
  price: number;
  description: string;
};

export default function Product({
  id,
  image,
  title,
  price,
  description,
}: ProductProps) {
  const dispatch = useCartDispatch();

  function handleAddToCart() {
    --dispatch(addToCart({ id, title, price }));
  }

  return (
    <article className="product">
      <img src={image} alt={title} />
      <div className="product-content">
        <div>
          <h3>{title}</h3>
          <p className="product-price">${price}</p>
          <p>{description}</p>
        </div>
        <p className="product-actions">
          <button onClick={handleAddToCart}>Add to Cart</button>
        </p>
      </div>
    </article>
  );
}
````

### Creating a Type-Safe useSelector Hook


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMyNTU2MzQ1OCwxMDM5NTQ5ODEzLDE1OT
I2NzAxOSwtMTY4NTkzOTMwMSw1NzAxNjY5NTcsLTEzOTMxMDAx
MjcsLTE4MTk1Mjk0NjIsLTE2OTgwNDk4OTMsLTE2Mjg4MzQ0Nj
gsLTE4Njc3NjQwMDIsLTIwMjQ0MTU5MjQsOTUzNDAxNTEzLC02
Mzk5MjQwMTMsLTE2NDI0OTU2NDEsLTEwNjgwNzI5NTcsLTE5Nj
A1MDM4MDMsLTQ1MTk3MzQ3NCwtMTA3MDA0NjYwLDExOTMxNjc0
OTQsMTExODkxMTA1Nl19
-->