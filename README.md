# fstack
Custom Stack type for f90 FORTRAN that impliments a C style stack using pure f90 FORTRAN. The advantage of this model is that you can have multiple stacks at any one time, so there is no need to juggle them, just allocate another one. Also, the stacks are all done with allocate and deallocate, so  you never have to have more memory used than you need, and if you need more space, just use `fs_realloc_stack` to make a stack larger.

## How to use:
* Download fstack.f90
* `use fstack`
* See below for functions and types.

## Types included:
* `fs_stack` : The main stack type. The parts of this type should not be acessed by you, but rather by the functions below. To declare one: `type(fs_stack) :: stack`

## Functions:
* `fs_create_stack(int)` : Creates a stack of size int. This is a function, so call like this:
*  `stack = fs_create_stack(size)`

## Subroutines:
* `fs_push(stack, real)` : Push real onto the stack.
* `fs_pop(stack, var)` : Pop top of stack into var.
* `fs_peek(stack, var)` : Put top of stack into var without modifying stack.
* `fs_reset_stack(stack)` : Reset stack to all 0's and reset stack pointer to 1.
* `fs_realloc_stack(stack, int)` : Realloc stack to size int, without modifying contents. ***THIS DOES NOT SUPPORT MAKING A STACK SMALLER!!! IT WILL GO OOB IF YOU TRY!!!***
* `fs_cleanup_stack(stack)` : Dealloc stack. Use at  end of programs.

## Internals:
* `fs_stack` is defined as 3 things : An allocatable array of `real`s, an `int` pointer to the current index and an `int` for tracking the current size of the array. All these are not private, but modifing them without the above functions is not recomended.
