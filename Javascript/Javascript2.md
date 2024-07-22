#### HTTP/2 

HTTP/2 is the latest "form" of the Http protocol and unlike HTTP 1, it allows for "server push". That means that servers can push required assets/ files actively to a client (instead of waiting for the client to request them).

You can learn more about it here: https://developers.google.com/web/fundamentals/performance/http2


The following resources may be helpful.

-   Google Performance Docs: [https://developers.google.com/web/fundamentals/performance/rendering](https://developers.google.com/web/fundamentals/performance/rendering)
-   Chrome DevTools Performance Docs: [https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference)
-   Chrome DevTools Memory Docs: [https://developers.google.com/web/tools/chrome-devtools/memory-problems](https://developers.google.com/web/tools/chrome-devtools/memory-problems)

## Testing

To automate testing

we need 3 things:

Test runner: execute tests, summarize results. e.g Mocha, Jest.

Assertion library: define testing logic, conditions. Eg. Chai, Jest

Headless browser, for e2e tests. Simulate user interaction. eg. Puppeteer

Max has some util functions to be tested using commonJS exports, because that'd need some extra set up otherwise

### Unit tests: functions with no dependencies

Dependencies are interacting with db, calling other fns, etc

Unit testing: pure functions testing

we can name the test file `.spec.js` or `.test.js`, Jest will look for both

Jest uses common JS imports

Jest will make test() fn globally available

`````js
// package.json
{
  "name": "js-testing-introduction",
  "version": "1.0.0",
  "description": "An introduction to JS testing",
  "main": "app.js",
  "scripts": {
    "start": "webpack app.js --mode development --watch",
      // jest will look for .spec or .test files and execute them
    👉"test": "jest "
  }
}
`````

````js
// util.js
// exported with commonJS, because Jest natively uses commonJS
exports.generateText = (name, age) => {
  // Returns output text
  return `${name} (${age} years old)`;
};
````

```js
// util.test.js
const { generateText } = require('./util');

const { generateText } = require('./util');

// test fn is provided by the test runner
test('should output name and age', () => {
    const text1 = generateText('Max', 29);
    // expect fn is provided by the assertion libray
    expect(text1).toBe('Max (29 years old)');

    const text2 = generateText('Anna', 28);
    expect(text2).toBe('Anna (28 years old)');
});

test('should output dataless text', () => {
    const text1 = generateText('', null);
    expect(text1).toBe(' (null years old)');

    const text2 = generateText();
    expect(text2).toBe('undefined (undefined years old)');
})
```

````bash
npm run test
````



### Integration tests

#### 👉testing a function that uses one or more function/s that have already been unit tested👈

````js
exports.generateText = (name, age) => {
  // Returns output text
  return `${name} (${age} years old)`;
};

exports.createElement = (type, text, className) => {
  // Creates a new HTML element and returns it
  const newElement = document.createElement(type);
  newElement.classList.add(className);
  newElement.textContent = text;
  return newElement;
};

exports.validateInput = (text, notEmpty, isNumber) => {
  // Validate user input with two pre-defined rules
  if (!text) {
    return false;
  }
  if (notEmpty && text.trim().length === 0) {
    return false;
  }
  if (isNumber && +text === NaN) {
    return false;
  }
  return true;
};

// 💡 👇instead of using this.validateInput, I could have used
// const validateInput = ...
// referenced validateInput inside checkAndGenerate
// exports.validateInput; // so I can use in other files

👉exports.checkAndGenerate = (name, age) => {
  // let's check
  if (!this.validateInput(name, true, false) || !this.validateInput(age, false, true)) return
  return this.generateText(name, age);
}
````

````js
const { generateText, validateInput, checkAndGenerate } = require('./util');

// 1️⃣unit tests
// test fn is provided by the test runner
test('should output name and age', () => {
    const text1 = generateText('Max', 29);
    // expect fn is provided by the assertion libray
    expect(text1).toBe('Max (29 years old)');

    const text2 = generateText('Anna', 28);
    expect(text2).toBe('Anna (28 years old)');
});

test('should output dataless text', () => {
    const text1 = generateText('', null);
    expect(text1).toBe(' (null years old)');

    const text2 = generateText();
    expect(text2).toBe('undefined (undefined years old)');
})

test('should validate name and age', ()=> {
    const result1 = validateInput('Max', true, false)
    expect(result1).toBe(true);

    const result2 = validateInput('Max', false, false)
    expect(result2).toBe(true);
    
    const result3 = validateInput('', false, false)
    expect(result3).toBe(false);

    const result4 = validateInput(28, false, true)
    expect(result4).toBe(true);

    const result5 = validateInput(28, false, false)
    expect(result5).toBe(true);
    
    const result6 = validateInput(null, false, false)
    expect(result6).toBe(false);

    const result7 = validateInput(undefined, false, false)
    expect(result7).toBe(false);

    const result8 = validateInput(null, true, false)
    expect(result8).toBe(false);

    const result9 = validateInput(undefined, false, false)
    expect(result9).toBe(false);
})


// 2️⃣integration test now!
// I've already unit tested generateText and validateInput fns in unit tests
// so I test how they work when used together inside another fn
👉 test('should output validated name and age', () => {
    const result1 = checkAndGenerate('Max', 29);
    expect(result1).toBe('Max (29 years old)')

    const result2 = checkAndGenerate('', 29);
    expect(result2).toBe(undefined)
})
````

​	

### e2e (end to end) tests

we can set up timeouts, like this:

````js
test('should print name an age', ()=>{}, 👉10000)
````

`````js
// util.test.js
// e2e test here!
test('should print name an age', async ()=>{
    const browser = await puppeteer.launch({
        headless: true, // could be set to false. Couldn't get it to launch on my Mac
        // slowMo: 80,
        // args: ['--window-size=1920,1080']
    })

    const page = await browser.newPage();

    await page.goto('file:///Users/estebanmunchjones/Documents/Coding/javascript-the-complete-guide-code/testing-02-unit-tests/index.html')

    await page.click('input#name')
    await page.type('input#name', 'Anna');

    await page.click('input#age')
    await page.type('input#age', '28');

    await page.click('#btnAddUser')

    const text = await page.$eval('.user-item', el => el.textContent);

    expect(text).toBe('Anna (28 years old)')
}, 10000)
`````

issues I faced: 

- I had some pupetter error at the beginning: https://stackoverflow.com/questions/74078944/cannot-find-module-puppeteer-core-internal-common-device-js
- then I had a localStorage one: localStorage is not available for opaque origins
- In the end I just installed Max's versions of jest and puppeteer

### Reaching out to the DOM breaks unit and integration tests!

````
const { fetchData } = require('./http');

❌const button = document.querySelector('button');

const loadTitle = () => {
  return fetchData().then(extractedData => {
    const title = extractedData.title;
    const transformedTitle = title.toUpperCase();
    return transformedTitle;
  });
};

const printTitle = () => {
  loadTitle().then(title => {
    console.log(title);
  });
};

❌button.addEventListener('click', printTitle);

exports.printTitle = printTitle;
````

````js
// testing printTitle will fail ❌

const { printTitle } = require('./app');

test('should print title', ()=>{
    const title = printTitle(); 
})
````

````bash
npm run test
  TypeError: Cannot read properties of null (reading 'addEventListener'); // document is null

      17 | };
      18 |
    > 19 | button.addEventListener('click', printTitle);
````

Keep working on trying to test printTitle not returning a promise, then then test loadtitle

Let's now try to test this fn:

````js
const printTitle = () => {
  // ❌it doesn't return, how can I use this fn when calling expect()??
  loadTitle().then(title => {
    // return title; // ❌ even a return here doesn't work, it needs to be at the root level of the fn body
    console.log(title);
  });
};
````

the solution is to test this fn instead:

````js
// util.js
const loadTitle = () => {
  // it return the promise at the root level of the fn body ✅
  return fetchData().then(extractedData => {
    const title = extractedData.title;
    const transformedTitle = title.toUpperCase();
    return transformedTitle;
  });
};
````

```js
//util.test.js
const { loadTitle } = require('./util');

test('should load title', async ()=>{
    const title = await loadTitle();
    expect(title).toBe('DELECTUS AUT AUTEM')
})
```

### Let's not hit the API every time we run the test!

it's nice to mock http requests, reaching out to the filesystem, intereacting with databases, etc

let's replace `fetchData` fn with a mock

jest does a file swapping

Steps:

1. create a `__mocks__` folder at the root level of the project, then add some files inside, that matches the name of the js files we want to replace. eg. http.js
2. then add `jest.mock('./http.js'); at the beginning of the test file

````js
// http.js
const axios = require('axios');

const fetchData = () => {
  return axios
    .get('https://jsonplaceholder.typicode.com/todos/1')
    .then(response => {
      return response.data;
    });
};

exports.fetchData = fetchData;
````

````js
// __mocks__/http.js

const fetchData = () => {
  return Promise.resolve({title: 'delectus aut autem'})
};

exports.fetchData = fetchData;
````

```js
// util.test.js
👉jest.mock('./http');

const { loadTitle } = require('./util');

test('should load title', async ()=>{
    const title = await loadTitle();
    expect(title).toBe('DELECTUS AUT AUTEM')
})
```

### Mock some node modules, like axios

No need to add `jest.mock('axios')` inside the test file, jest will do it automatically! 🎉

````js
// util.test.js
// jest.mock('./http'); 🎉

const { loadTitle } = require('./util');

test('should load title', async ()=>{
    const title = await loadTitle();
    expect(title).toBe('DELECTUS AUT AUTEM')
})
````

````js
// __mocks__/axios.js
exports.get = (url) => {
    console.log('using mocked axios')
    switch(url){
        case 'https://jsonplaceholder.typicode.com/todos/1':
            return Promise.resolve({data: {title: 'delectus aut autem'}})
    }
}
````

The following resources may be helpful.

-   Article on JS Testing: [https://academind.com/learn/javascript/javascript-testing-introduction/](https://academind.com/learn/javascript/javascript-testing-introduction/)
-   Official Jest Docs: [https://jestjs.io/docs/en/getting-started](https://jestjs.io/docs/en/getting-started)
-   Testing with Spies, Stubs & Mocks: [https://www.harrymt.com/blog/2018/04/11/stubs-spies-and-mocks-in-js.html](https://www.harrymt.com/blog/2018/04/11/stubs-spies-and-mocks-in-js.html)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUzMzYxMDcwNCw0MzY3MDg4NDksLTkxNT
M4NjQ3NCwtMTU4Mzc0MDA0OCwtMTgzMzcyOTA1MF19
-->