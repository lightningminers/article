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

#### 配置


First install all the dependencies including peer dependencies:

第一步安装所有的依赖包括同版本依赖:

```
npm install --save-dev jest react-test-renderer enzyme enzyme-adapter-react-16 enzyme-to-json
```

You’ll also need [babel-jest](https://github.com/facebook/jest/tree/master/packages/babel-jest) for Babel and [ts-jest](https://github.com/kulshekhar/ts-jest) for TypeScript.

你也需要安装 Babel 插件 [babel-jest](https://github.com/facebook/jest/tree/master/packages/babel-jest) 或者 TypeScript 插件 [ts-jest](https://github.com/kulshekhar/ts-jest)

Update your package.json:

更新工程的 package.json 文件:

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

配置项 'snapshotSerializers' 允许你直接传递 Enzyme 的封装类型 'enzyme-to-json' 到 'Jest' 的快照匹配项中，从而不需要手动进行转化。

Create a test/jestsetup.js file to customize Jest environment (see setupFiles above):

创建一个 test/jestsetup.js 的文件来自定义 Jest 的运行环境（上面的 setupFiles 配置项）

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

针对 css 模块也可以添加下面的配置到package.json

```
"jest": {
  "moduleNameMapper": {
    "^.+\\.(css|scss)$": "identity-obj-proxy"
  }
}
```

And run:

同时安装依赖:

```
npm install --save-dev identity-obj-proxy
```

Note that [identity-obj-proxy](https://github.com/keyanzhang/identity-obj-proxy) requires node — harmony-proxies flag for Node 4 and 5.

注意 [identity-obj-proxy](https://github.com/keyanzhang/identity-obj-proxy) 依赖的 node 版本是 Node 4或者 Node 5需要开启 'harmony-proxies'

#### Writing tests

#### 单元测试

#### Testing basic component rendering

#### 测试组件的渲染

That’s enough for most non-interactive components:

对于大部分没有交互的组件，下面的测试用例已经足够:

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

#### Props 测试

Sometimes you want to be more explicit and see real values in tests. In that case use Enzyme API with regular Jest assertions:

有的时候如果你想测试的更精确和看到真实的值。那样的话需要在 Enzyme API 中使用 Jest的 断言。

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

有的时候你不能用快照。比如组件里面有随机ID像下面的代码:

```
test('render a popover with a random ID', () => {
    const wrapper = shallow(
        <Popover>Hello Jest!</Popover>
    );
    expect(wrapper.prop('id')).toMatch(/Popover\d+/);
});
```

#### Testing events

#### 事件测试

You can simulate an event like click or change and then compare component to a snapshot:

你可以模拟类似 'click' 或者 'change'这样的事件然后把组件比作一个快照:

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

有的时候你想要测试一个子组件中一个元素是怎样影响组件的。你需要使用 Enzyme的 mount 方法来渲染一个真实的 DOM。

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

#### 测试事件处理

类似于在事件测试中，由使用快照测试组件的输出呈现替换为使用Jest的mock函数来测试事件处理程序本身：

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

#### 不仅仅是JSX

Jest使用JSON进行快照测试，因此你可以测试返回JSON的任何函数，方法与测试组件相同：
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

#### 调试与故障排除

**调试浅层渲染器输出**

Use Enzyme’s debug method to print shallow renderer’s output:
使用Enzyme的调试方法打印千层渲染器的输出：

```
const wrapper = shallow(/*~*/);
console.log(wrapper.debug());
```

**启用覆盖范围的失败测试**

当你的测试失败时，带有覆盖范围标志的diff如下所示：

```
-<Button
+<Component
```

尝试将箭头函数组件替换为常规函数组建：

```
- export default const Button = ({ children }) => {
+ export default function Button({ children }) {
```

**requestAnimationFrame 错误**

当你运行你的测试时，你可能会看到如下错误：

```
console.error node_modules/fbjs/lib/warning.js:42
  Warning: React depends on requestAnimationFrame. Make sure that you load a polyfill in older browsers. http://fb.me/react-polyfills
```
React 16[依赖于](https://reactjs.org/docs/javascript-environment-requirements.html)`requestAnimationFrame`，因此你需要在你的测试代码中添加一个[polyfill](https://github.com/chrisdickinson/raf)
```
// test/jestsetup.js
import 'raf/polyfill';
```

#### 参考来源

- [Jest cheat sheet](https://github.com/sapegin/jest-cheat-sheet)
- [Testing React Applications](https://youtu.be/59Ndb3YkLKA) by Max Stoiber
- [Migrating to Jest](https://medium.com/@kentcdodds/migrating-to-jest-881f75366e7e#.pc4s5ut6z) by Kent C. Dodds
- [Migrating Ava to Jest](http://browniefed.com/blog/migrating-ava-to-jest/) by Jason Brown




