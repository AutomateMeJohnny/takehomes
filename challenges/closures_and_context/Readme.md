## Question 1:

Consider the following code:

    function foo() {
        console.log(fred);
        console.log(bar());
        
        var fred = 6;
        function bar() {
            return 7;
        }
    }
    
    foo();

What is the result of executing this code? Please explain your reasoning.



<details> 
  <summary>***** Answer ******</summary>  
  Running the Foo Function returns two logs to the console.
  The first console.log(fred) logs “undefined” because of hoisting. The function is evaluated with variable fred at the top of the function scope initialized but not assigned a value until later in the function.
  The second console.log(bar()) logs “7”, also because of hoisting but in the case of function declarations, the whole function is hoisted.
  *******************
</details>


## Question 2:

Consider the following code:

    var name = 'Fred';
    var obj = {
        name: 'George',
        prop: {
            name: 'Bill',
            getName: function() {
                return this.name;
            }
        }
    }
    
    console.log(obj.prop.getName());
    
    var test = obj.prop.getName;
    console.log(test());
    
What is the result of executing this code? Please explain your reasoning.


<details> 
  <summary>***** Answer ******</summary>  
  For console.log(obj.prop.getName()), it logs “Bill” because this.name is referring to which closure it was called from. In this case it was “obj.props” which the name is “Bill”.  
  For console.log(test()), the same applies. In this case the function declaration was grabbed and put into a variable called test. Since test is not in a wrapping object or closure it defaults to the global “window” object. So when test() is invoked the “this” keyword is pointing to “window” which has the property of “name = ‘Fred’”.  
  *******************
</details>
