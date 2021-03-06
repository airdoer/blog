# React初探

by bingochaos

React、Vue和Angular应该是近几年来最火的三个前端框架了，React一直保持着较高的热度，发展迅猛，而Vue则更像是一匹黑马占据了大量市场，反而是之前更热的Angular，关注度大不如前了。本次主要探究的是React框架的内容。

> A JavaScript library for building user interfaces

一个为UI而生的库，React作为一个前端框架，就是为了解决最本质的前端诉求。官方描述中有三个特点： **声明式，组件化和一次学习 ，随处编写**。本文先讲一下我对这三个特点的理解。


## 声明式(Declarative)

主要的编程范式有：

 * 命令式编程
 * 声明式编程
 * 函数式编程
 * 面向对象编程

### 命令式编程

```Javascript
toLowerCase(['FOO', 'BAR']);   //['foo','bar']
```

命令式函数实现：

```Javascript
const toLowerCase = arr => {
    const res = [];
    for (let i = 0, len = arr.length; i < len; i++) {
        res.push(arr[i].toLowerCase());
    }
    return res;
}
```

首先创建一个空数组用于保存结果，然后遍历输入数据的所有元素，将每项元素的小写值存入空数组中，然后返回结果。

### 声明式编程

```Javascript
const toLowerCase = arr => arr.map(
    value => value.toLowerCase();
}
```

输入数组的元素传递给map的函数，然后返回包含小写值的新数组


### 从 raw js 到 react

示例：带有标记的地图

#### raw js

```Javascript
const map = new Map.map(document.getElementById('map'), {
    zoom: 4,
    center: {lat, lng}
});

const marker = new Map.marker({
    position:{lat, lng},
    title: 'Marker'
});

marker.setMap(map);
```

#### React

```xml
<Map zoom={4} center={lat, lng}>
    <Marker position={lat, lng} title={'Hello Marker'} />
</Map>
```

### declare programming 小结

从代码书写的角度看声明式编程就像是告诉了标签，我要一个什么样的UI你给我变出来。命令式就是你这么变这么变，好了是我要的样子了。 
> 采用declare方式，代码看上去更短，其本质是在命令式代码之上添加了添加了rendering的过程，其本质还是html，只是React把自定义的标签转化成标准Html的过程

## 组件化 (Component-Based)

驱动React高效性能的虚拟DOM技术最基础的单元就是一个个组件，而使用组件化最直观的就是标签化

```html
<div class='map'></div>

变成

<Map> </Map>
```

在使用的时候无需关注组件内部的实现，只要添加标签就能响应对应的事件，展示对应的UI

### React

```Javascript
Class Page extends Component {
    render() {
        <div>
            <Map onTouch={Touch} onClick={Click}/>
        </div>
    }
}
```

组件包含两个重要内容props和state，个人理解props就是用于组件展现自身的，而使用怎样的props就是根据state分发组装完成的。


## 一次学习，随处编写

感觉就是给React Native打广告的。。以后再谈


## JSX简介（来自官网）

```Javascript
// This funny tag syntax is neither a string nor HTML.
const element = <h1>Hello, world!</h1>;
```

上面这种写法就是JSX，是JavaScript的一种扩展，React中会大量用到这个。

### Render()

```Javascript
function tick() {
    const element = {
        <div>
            <h1>Hello,world!</h1>
            <h2>It is {new Date().toLocaleTimeString()}.</h2>
        </div>
    };
    ReactDOM.render(element, document.getElementById('root'));
}
setInterval(tick, 1000);
```

当发生UI变化是即使每秒改变整个DOM，React DOM也只会渲染差异部分，有效降低了开发成本。

### props

```Javascript
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
}

function App() {
    return (
        <div>
            <Welcome name="Sara" />
            <Welcome name="Cahal" />
            <Welcome name="Edite" />
        </div>
    );
}
ReactDOM.render(<App />, document.getElementById('root'));
```

在React 中不允许修改Props，保持其为只读的

### state

```Javascript
class Clock extends React.Component {
    constructor(props) {
        super(props);
        this.state = {date: new Date()};    
    }

    render() {
        return (
            <div>
                <h1>Hello,world!</h1>
                <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
            </div>
        );
    }
}

ReactDOM.render(
    <Clock />,
    document.getElementById('root')
);
```

若要改变Component状态，应该是用state代替props，state属于Component对象属性。再具体使用中可以配合生命周期函数配合使用，在修改state状态时，使用this.setState({comment:'Hello'});而非this.state.comment = 'Hello';


## 总结

本文大概描述了一些React入门的概念，后续将会深入挖掘React的开发。






















