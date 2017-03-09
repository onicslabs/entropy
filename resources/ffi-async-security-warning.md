The following excerpt is a word of caution from `The Rust Book` about using Rust's FFI features in asynchronous calling code. Special care has to be paid to data access and ensuring objects are dereferenced after destruction.

"""
If an asynchronous callback targets a special object in the Rust address space it is also absolutely necessary that no more callbacks are performed by the C library after the respective Rust object gets destroyed. This can be achieved by unregistering the callback in the object's destructor and designing the library in a way that guarantees that no callback will be performed after deregistration.
"""

https://doc.rust-lang.org/book/ffi.html#asynchronous-callbacks
