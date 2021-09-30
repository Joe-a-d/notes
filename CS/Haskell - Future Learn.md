**Tags** : #JeremySinger #MOOC #uni #FP #PL #haskell

# Week 1

- [[statements vs expressions]] 
	- expressions are the actual computations while statements manipulate the flow of execution and control
	- statements : think of loops, conditionals 
	- expressions : think `x + x`
	-  **Motivation**
		-  pure functional languages do not use statements, no assignments, no jumps. Instead they rely only on evaluating expressions
		- [ ] **Why?** 
			- no need for state?
- [[expressions]]
	- **Notation** 
		- `e --> r` : expression `e` evaluates to result `r`
		- $e \rightsquigarrow r$ , formally
	-  **Example**
		-  ``3+4 --> 7``

- [[functions]]
	- very close to the same concept in mathematics
	- take an argument , compute, return result
	- **Syntax**
		-  *call* : `<identifier> <arg1 arg2 ...>`
			-  arguments are separeted by spaces
		- `max 1 2 --> 2 ` 
	- **function application binds tighter than anything else**
		- (though this might not be phrased properly) if you think of func app as an operation in itself, then it will have the highest precedende. Such that, if the function is an expression you need to enclose it in parenthesis
		- `f x + 3` == `(f x) + 3` ≠ `f (x + 3)`
		- anonymous functions are represented as [[lambda functions#^c8ef29]]

- [[equations]]
	- their purpose is to name the expressions
	- though the labels are often called *variables* this is somewhat of a misnomer , since the names can not vary.  An equation indicates a relation of equality between the label and the expression, hence whenever the label is used elsewhere we know that it is just a placeholder for the expression
	- **this is in contrast** with other styles of programming where variables are just holders representing assignments which can change throughout the life of the program , e.g. `i += 1` in mathematical terms makes no sense in the same way that `1 = 2` makes no sense. Though it is ok if this is an assignment since we are just saying *"compute the RHS then store it in the left hand side, overwriting the old value"*
		- note though that `i = i +1` is still valid haskell, the compiler will define `i` , but when trying to evaluate the expression will fail, since it is not able to compute the value of `n` which satisfies `n = n + 1`
	- it might be useful to think of the labels instead as *definitions*

- **computing without assignments**
	- values are never discarded
	- instead of reassigning old values new ones are created and old ones if "useless" (I think he means if not used during the rest of the program) are reclaimed by the [[garbage collector]]

- [[variable binding]] seems to be similar to assignments but their scope is limited to the expression in which they are used
	-  `let x = 4 in x * x` binds `x` to `4` so that `x` in the expression just gets replaced by `4` , but when asking for the value of `x` in another prompt there's nothing
	-  Hence **syntax** : `let <var> = <expr> in <body>` where `var == expr` in `body`
- [[cons]] `(:)` is a function which takes two values
	-  a value and a list : `<val> : []`
	-  returns a new list out of the value passed
	-  the **motivation** here is to show that this is one of the fundamental building blocks, but syntatic sugar exists to make this sort of thing easy
		- `'a' : 'b' : [ ] ` == `['a', 'b']` 
		-  [ ] it is not clear why this works! if `:` takes a value and a list. Maybe evaluates from the right, so that we have `a : (b : [ ])` , but how is precedence determined?
-  **code blocks** use the `let ... in ...` 
	-  inside `let` we can define multiple expressions
	-  the value to be *"returned*", i.e. the final value of the expression is put after the `in`


# Resources

- [for more on the effects of using just expressions](https://fsharpforfunandprofit.com/posts/expressions-vs-statements/)