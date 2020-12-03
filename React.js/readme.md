# Features
- Declarative
- Component-based
- Learn Once, Write Anywhere

# CDN
JSXをコンパイルするためにbabelも必要、typeはtext/babelにする
```html
<script crossorigin src="https://unpkg.com/react@17/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
<script type="text/babel" defer src="./main.js"></script>
```

# Class vs Function
```js
// class
class HelloReact extends React.Component {
    render() {
        return (
            <h1>hello,World!!!</h1>
        )
    }
}
ReactDOM.render(<HelloReact/>, document.getElementById("root"));

// function
function helloReact() {
    return (<h1>hello, world</h1>)
}

const elm = (
    {helloReact()}
);

ReactDOM.render(elm, document.getElementById("root"));
```

# props
```js
function Show(props) {
    return (
        <h3>
            Name is {props.name}
        </h3>
    );
}

Show.defaultProps = {
    name: "defaultName"
}

function App() {
    return (
        <main>
            <Show name="a" />
            <Show name="b" />
            <Show name="c" />
        </main>
    );
}

const elm = <Show name="MyName" />

ReactDOM.render(<App />, document.getElementById("root"));
```
