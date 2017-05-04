# **babel-plugin-css-generator-react-components**

Generate .css files from API, styles in JS Edit

## Example

The following input:
 ```javascript
 //INPUT.JS
 class Foo extends React.Component {
    constructor(props) {
        super(props);
    }

    componentDidMount() {
        console.log("mounted");
    }

    marianoStyle() {
        STYLED_DIV = {
            'color': red,
            'position': relative,
            'background-position': center
        };
        STYLED_SPAN = {
            'color': black,
            'background-color': red
        };
    }

    render() {
        return (
            <STYLED_DIV> HOLA </STYLED_DIV>)
    }
}
 ```
 
 Results in the following output:
 
 ```css
 /*foo.css*/
 .foo-styled_div{color : red;position : relative;background-position : center;}
.foo-styled_span{color : black;background-color : red;}
 ```
 
 ```css
 /*root.css*/
 @import './foo.css';
 ```
 
 ```javascript
 //BABEL OUTPUT
 class Foo extends React.Component {
    constructor(props) {
        super(props);
    }

    componentDidMount() {
        console.log("mounted");
    }

    render() {
        return React.createElement(
            'div',
            {
                className: 'foo-styled_div'
            },
            ' HOLA '
        );
    }
}
 ```
