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

## Why it's effective

- **Separation of Concerns:** Operations (services) are separated from the objects (rooms). The objects don't need to know how to perform these operations.
  **Extensibility:** It's easy to add new operations (new types of services) without changing the objects. You just add a new visitor.
  **Single Responsibility:** Each visitor class can focus on one kind of operation, making it easier to understand and maintain.
  **Flexibility:** You can have different visitors performing different operations on the same set of objects.

## Example

```ts
// Define the Media types
interface Audio {
  type: "audio";
  playSound(): void;
}

interface Video {
  type: "video";
  displayVideo(): void;
}

// Visitor interface
// Visitor can either be of type Audio or Video
interface MediaVisitor {
  visitAudio(audio: Audio): void;
  visitVideo(video: Video): void;
}

// Concrete Media objects
const myAudio: Audio = {
  type: "audio",
  playSound: () => console.log("Playing audio..."),
};

const myVideo: Video = {
  type: "video",
  displayVideo: () => console.log("Displaying video..."),
};

// Concrete Visitor
const mediaPlayer: MediaVisitor = {
  // audio here is myAudio
  visitAudio: (audio) => audio.playSound(), // This ties back to `myAudio` object

  // video here is myVideo
  visitVideo: (video) => video.displayVideo(), // This ties back to `myVideo` object
};

// Function to accept visitors
function acceptMediaVisitor(media: Audio | Video, visitor: MediaVisitor) {
  // `media` here is myAudio
  if (media.type === "audio") {
    visitor.visitAudio(media); // This calls `mediaPlayer.visitAudio(myAudio)`
  } else if (media.type === "video") {
    // `media` here is myVideo
    visitor.visitVideo(media); // This calls `mediaPlayer.visitVideo(myVideo)`
  }
}

// Using the Visitor
acceptMediaVisitor(myAudio, mediaPlayer); // Outputs: Playing audio...
acceptMediaVisitor(myVideo, mediaPlayer); // Outputs: Displaying video...
```
