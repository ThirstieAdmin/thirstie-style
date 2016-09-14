# Javascript conventions and style guide

## tooling

* es6 (es2015)
* express +  react w/ jsx 
* npm + gulp + webpack
  * only use gulp for complex builds
  * otherwise use npm scripts + webpack for builds
* tape test framework: https://github.com/substack/tape
  * prefer tests with equal or deepEqualtests between actual and expected output.
* hogan for templates
* forever for process management


## code conventions

* We could start with [eslint](http://eslint.org/docs/rules/)  defaults
  * General modifications
    * use 2?? spaces for indents 
    * prefer object literal notation over factory functions and factory functions over constructor functions
  
      ```
      // do this, unless you need multiple copies
      let dataHandler = {
        x: null,
        y: null,
        op: function(x, y) {
          this.x = x;
          this.y = y;
          return this.x + this.y;
        }
      }
      
      // or this, if you need multiple copies
      let createDataHandler = function () {
        let dataHandler = {
          x: null,
          y: null,
          op: function(x, y) {
            this.x = x;
            this.y = y;
            return this.x + this.y;
        }
        return dataHandler;
      }
      let dh1 = createDataHandler();
      let dh2 = createDataHandler();
      
      // not this
      let DataHandlerObj = function () {
      this.x = null;
      this.y = null;
      this.op = function (arg1, arg2) {
      this.x = arg1;
      this.y = arg2;
      return this.x + this.y;
      }
      }
      let dh1 = new DataHandlerObj();
      let dh2 = new DataHanlderObj();
      ```

  * ES6 / JSX modifications
    * use `const` if possible, if not use `let`, if `let` is not appropriate, review your logic and use `var` as a last resort
    * use .js extension even if JSX is used
    * use Babel to compile all code with es2015 presets
    * prefer factory functions over ES6 class  constructors
    * avoid mixins, compose classes instead
    * use explicit destructuring statements:
    
      ```  
      // explicitly declare all variables
      let {a, b} = {a: 'ay', b: 'bee'};
      
      // not
      ({a, b} = {a: 'ay', b: 'bee});
      ```
