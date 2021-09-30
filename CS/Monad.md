`Maybe T` can be understood as a "wrapping" type, wrapping the type `T` into a new type with built-in exception handling, though carrying no information about the cause of an exception.

Another improvement would be if a function could manage simple [checked exceptions](https://en.wikipedia.org/wiki/Checked_exception "Checked exception") with a `Maybe` type, [short-circuiting](https://en.wikipedia.org/wiki/Short-circuit_evaluation "Short-circuit evaluation") and returning `Nothing` once a step fails, but returning the correct value without comment if a calculation succeeds.

An addition function `add`, which does exactly this when adding two `Maybe` values, `mx` and `my`, can be defined like so:

 add : (Maybe Number, Maybe Number) → Maybe Number
 
 The Prelude contains a number of classes defining monads are they are used in Haskell. These classes are based on the monad construct in category theory; whilst the category theoretic terminology provides the names for the monadic classes and operations, it is not necessary to delve into abstract mathematics to get an intuitive understanding of how to use the monadic classes.

A monad is constructed on top of a polymorphic type such as IO. The monad itself is defined by instance declarations associating the type with the some or all of the monadic classes, Functor, Monad, and MonadPlus. None of the monadic classes are derivable. In addition to IO, two other types in the Prelude are members of the monadic classes: lists ([]) and Maybe.

Mathematically, monads are governed by set of _laws_ that should hold for the monadic operations. This idea of laws is not unique to monads: Haskell includes other operations that are governed, at least informally, by laws. For example, x /= y and not (x == y) ought to be the same for any type of values being compared. However, there is no guarantee of this: both == and /= are separate methods in the Eq class and there is no way to assure that == and =/ are related in this manner. In the same sense, the monadic laws presented here are not enforced by Haskell, but ought be obeyed by any instances of a monadic class. The monad laws give insight into the underlying structure of monads: by examining these laws, we hope to give a feel for how monads are used.

The Functor class, already discussed in section [5](https://www.haskell.org/tutorial/classes.html#tut-type-classes), defines a single operation: fmap. The map function applies an operation to the objects inside a container (polymorphic types can be thought of as containers for values of another type), returning a container of the same shape. These laws apply to fmap in the class Functor: