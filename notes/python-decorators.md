## decorators example

### simple decorator with no args 

```
def function_decorator(function):
    def wrapper(*args , **kwargs):
        func = function
        print("This is a wrapper function") 
        print("arguments : " , args)
        print("keyword args : " , kwargs)       
        return func
    return wrapper




@function_decorator
def add_one(num):
    print(num + 1)
    return num + 1


add_one(1)
```


### decorator with arguments

```
import functools
def decorator_with_args(*dargs):
    def function_decorator(function):
        @functools.wraps(function)
        def wrapper(*args , **kwargs):
            func = function
            print("This is a wrapper function") 
            print("decorator args : " , dargs)
            print("arguments : " , args)
            print("keyword args : " , kwargs)       
            return func
        return wrapper
    return function_decorator


@decorator_with_args("log")
def add_one(num):
    print(num + 1)
    return num + 1

print(add_one.__name__)
add_one(1)

```