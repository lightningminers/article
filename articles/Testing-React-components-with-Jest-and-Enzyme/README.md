---
type: FrontEnd
title: Testing React components with Jest and Enzyme
link: https://hackernoon.com/testing-react-components-with-jest-and-enzyme-41d592c174f
author: [Artem Sapegin](https://hackernoon.com/@sapegin)
---

# Testing React components with Jest and Enzyme

Some people say that testing React components is useless and in many cases it is, but there are a few cases when I think it’s useful:

- component libraries,
- open source projects,
- integration with 3rd party components,
- bugs, to prevent regressions.

I’ve tried many tools and finally have found a combination that I like enough to suggest to other developers:

- [Jest](https://facebook.github.io/jest/), a test runner;
- [Enzyme](http://airbnb.io/enzyme/), a testing utility for React;
- [enzyme-to-json](https://github.com/adriantoine/enzyme-to-json) to convert Enzyme wrappers for Jest snapshot matcher.

For the most of my tests I use shallow rendering with Jest snapshots.

![img](../Testing-React-components-with-Jest-and-Enzyme/assets/i_1.png)

Snapshot testing in Jest

#### Shallow rendering

Shallow rendering renders only component itself without its children. So if you change something in a child component it won’t change shallow output of your component. Or a bug, introduced to a child component, won’t break your component’s test. It also doesn’t require DOM.

For example this component:

```
const ButtonWithIcon = ({icon, children}) => (
    <button><Icon icon={icon} />{children}</button>
);
```

Will be rendered by React like this:

```
<button>
    <i class="icon icon_coffee"></i>
    Hello Jest!
</button>
```

But like this with shallow rendering:

```
<button>
    <Icon icon="coffee" />
    Hello Jest!
</button>
```

Note that the Icon component was not rendered.

#### Snapshot testing

Jest snapshots are like those old text UIs with windows and buttons made of text characters: it’s a rendered output of your component stored in a text file.

You tell Jest that you want to be sure that output of this component should never change accidentally and Jest saves it to a file that looks like this:

```
exports[`test should render a label 1`] = `
<label
  className="isBlock">
  Hello Jest!
</label>
`;

exports[`test should render a small label 1`] = `
<label
  className="isBlock isSmall">
  Hello Jest!
</label>
`;
```

Every time you change your markup Jest will show you a diff and ask you to update a snapshot if the change was intended.

Jest stores snapshots besides your tests in files like **snapshots**/Label.spec.js.snap and you need to commit them with your code.

#### Why Jest

- Very fast.
- Snapshot testing.
- Awesome interactive watch mode that reruns only tests that are relevant to your changes.
- Helpful fail messages.
- Simple configuration.
- Mocks and spies.
- Coverage report with a single command line switch.
- Active development.
- Impossible to write silently wrong asserts like expect(foo).to.be.a.function instead of expect(foo).to.be.a(‘function’) in Chai because it’s the only natural thing to write after (correct) expect(foo).to.be.true.

#### Why Enzyme

- Convenient utilities to work with shallow rendering, static rendered markup or DOM rendering.
- jQuery-like API to find elements, read props, etc.

#### Setting up

First install all the dependencies including peer dependencies:

```
npm install --save-dev jest react-test-renderer enzyme enzyme-adapter-react-16 enzyme-to-json
```

You’ll also need [babel-jest](https://github.com/facebook/jest/tree/master/packages/babel-jest) for Babel and [ts-jest](https://github.com/kulshekhar/ts-jest) for TypeScript.

Update your package.json:

```
"scripts": {
  "test": "jest",
  "test:watch": "jest --watch",
  "test:coverage": "jest --coverage"
},
"jest": {
  "setupFiles": ["./test/jestsetup.js"],
  "snapshotSerializers": ["enzyme-to-json/serializer"]
}
```

snapshotSerializers allows you to pass Enzyme wrappers directly to Jest’s snapshot matcher, without converting them manually by calling enzyme-to-json’s toJson function.

Create a test/jestsetup.js file to customize Jest environment (see setupFiles above):

```
import Enzyme, { shallow, render, mount } from 'enzyme';
import Adapter from 'enzyme-adapter-react-16';
// React 16 Enzyme adapter
Enzyme.configure({ adapter: new Adapter() });
// Make Enzyme functions available in all test files without importing
global.shallow = shallow;
global.render = render;
global.mount = mount;
```

For CSS Modules also add to jest section in your package.json:

```
"jest": {
  "moduleNameMapper": {
    "^.+\\.(css|scss)$": "identity-obj-proxy"
  }
}
```

And run:

```
npm install --save-dev identity-obj-proxy
```

Note that [identity-obj-proxy](https://github.com/keyanzhang/identity-obj-proxy) requires node — harmony-proxies flag for Node 4 and 5.

#### Writing tests

#### Testing basic component rendering

That’s enough for most non-interactive components:

```
test('render a label', () => {
    const wrapper = shallow(
        <Label>Hello Jest!</Label>
    );
    expect(wrapper).toMatchSnapshot();
});

test('render a small label', () => {
    const wrapper = shallow(
        <Label small>Hello Jest!</Label>
    );
    expect(wrapper).toMatchSnapshot();
});

test('render a grayish label', () => {
    const wrapper = shallow(
        <Label light>Hello Jest!</Label>
    );
    expect(wrapper).toMatchSnapshot();
});
```

#### Testing props

Sometimes you want to be more explicit and see real values in tests. In that case use Enzyme API with regular Jest assertions:

```
test('render a document title', () => {
    const wrapper = shallow(
        <DocumentTitle title="Events" />
    );
    expect(wrapper.prop('title')).toEqual('Events');
});

test('render a document title and a parent title', () => {
    const wrapper = shallow(
        <DocumentTitle title="Events" parent="Event Radar" />
    );
    expect(wrapper.prop('title')).toEqual('Events — Event Radar');
});
```

In some cases you just can’t use snapshots. For example if you have random IDs or something like that:

```
test('render a popover with a random ID', () => {
    const wrapper = shallow(
        <Popover>Hello Jest!</Popover>
    );
    expect(wrapper.prop('id')).toMatch(/Popover\d+/);
});
```

#### Testing events

You can simulate an event like click or change and then compare component to a snapshot:

```
test('render Markdown in preview mode', () => {
    const wrapper = shallow(
        <MarkdownEditor value="*Hello* Jest!" />
    );

    expect(wrapper).toMatchSnapshot();

    wrapper.find('[name="toggle-preview"]').simulate('click');

    expect(wrapper).toMatchSnapshot();
});
```

Sometimes you want to interact with an element in a child component to test effect in your component. For that you need a proper DOM rendering with Enzyme’s mount method:

```
test('open a code editor', () => {
    const wrapper = mount(
        <Playground code={code} />
    );

    expect(wrapper.find('.ReactCodeMirror')).toHaveLength(0);

    wrapper.find('button').simulate('click');

    expect(wrapper.find('.ReactCodeMirror')).toHaveLength(1);
});
```

#### Testing event handlers

Similar to events testing but instead of testing component’s rendered output with a snapshot use Jest’s mock function to test an event handler itself:

```
test('pass a selected value to the onChange handler', () => {
    const value = '2';
    const onChange = jest.fn();
    const wrapper = shallow(
        <Select items={ITEMS} onChange={onChange} />
    );

    expect(wrapper).toMatchSnapshot();

        wrapper.find('select').simulate('change', {
        target: { value },
    });

    expect(onChange).toBeCalledWith(value);
});
```

#### Not only JSX

Jest snapshots work with JSON so you can test any function that returns JSON the same way you test your components:

```
test('accept custom properties', () => {
    const wrapper = shallow(
        <Layout
            flexBasis={0}
            flexGrow={1}
            flexShrink={1}
            flexWrap="wrap"
            justifyContent="flex-end"
            alignContent="center"
            alignItems="center"
        />
    );
    expect(wrapper.prop('style')).toMatchSnapshot();
});
```

#### Debugging and troubleshooting

**Debugging shallow renderer output**

Use Enzyme’s debug method to print shallow renderer’s output:

```
const wrapper = shallow(/*~*/);
console.log(wrapper.debug());
```

**Failing tests with enabled coverage**

When your tests fail with — coverage flag with diff like this:

```
-<Button
+<Component
```

Try to replace arrow function component with regular function:

```
- export default const Button = ({ children }) => {
+ export default function Button({ children }) {
```

**requestAnimationFrame error**

You may see an error like this when you run your tests:

```
console.error node_modules/fbjs/lib/warning.js:42
  Warning: React depends on requestAnimationFrame. Make sure that you load a polyfill in older browsers. http://fb.me/react-polyfills
```

React 16 [depends on ](https://reactjs.org/docs/javascript-environment-requirements.html)`requestAnimationFrame`, so you need to add [a polyfill](https://github.com/chrisdickinson/raf) to your tests:

```
// test/jestsetup.js
import 'raf/polyfill';
```

#### Resources

- [Jest cheat sheet](https://github.com/sapegin/jest-cheat-sheet)
- [Testing React Applications](https://youtu.be/59Ndb3YkLKA) by Max Stoiber
- [Migrating to Jest](https://medium.com/@kentcdodds/migrating-to-jest-881f75366e7e#.pc4s5ut6z) by Kent C. Dodds
- [Migrating Ava to Jest](http://browniefed.com/blog/migrating-ava-to-jest/) by Jason Brown




