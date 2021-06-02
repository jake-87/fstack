# fstack
Custom Stack type for f90 FORTRAN that impliments a C style stack using pure f90 FORTRAN.

## How to use:
* Download fstack.f90
* `use fstack`
* See below for functions and types.

## Types included:
* `fs_stack` : The main stack type. The parts of this type should not be acessed by you, but rather by the functions below. To declare one: `type(fs_stack) :: stack`

## Functions:
* `fs_create_stack(int)` : Creates a stack of size int. This is a function, so call like this: `stack = fs_create_stack(5)`

## Subroutines:
* `fs_push(stack, real)` : Push real onto the stack.
* `fs_pop(stack, var)` : Pop top of stack into var.
* `fs_peek(stack, var)` : Put top of stack into var without modifying stack.
* `fs_reset_stack(stack)` : Reset stack to all 0's and reset stack pointer to 1.
* `fs_realloc_stack(stack, int)` : Realloc stack to size int, without modifying contents.
* `fs_cleanup_stack(stack)` : Dealloc stack. Use at  end of programs.
