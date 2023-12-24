# Visitor Pattern

Often used when dealing with AST (Abstract Syntax Tree) or other tree-like structures.

## Analogy

Think of the Visitor Pattern like a home repair service. You have different types of rooms in your house (like kitchen, living room, bathroom - these are your objects). Now, you need different services (like plumbing, painting, electrical work - these are your operations).

Instead of teaching each room how to fix itself (which is impractical), you call in different service professionals (plumbers, painters, electricians - these are your visitors). Each type of professional knows how to deal with each room type. When a professional visits a room, they perform the specific service that room needs.

## Explained

In the Visitor Pattern:

- Each "room" (object) has a method to accept a "service professional" (visitor).
- Each "service professional" (visitor) knows how to handle different types of "rooms" (objects) and has a method for each room type.
- When a visitor visits an object, the object calls the appropriate method on the visitor, passing itself. The visitor then performs its operation on the object.
