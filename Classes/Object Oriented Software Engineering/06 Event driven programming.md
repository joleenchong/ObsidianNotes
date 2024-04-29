Code can trigger and handle events. A [[Model-View-Controller Architecture]] app uses events in 2 ways:
- UI elements - triggers events when user does smth
- Model classes - triggers events when data changes


Event handlers cannot throw exceptions for external errors as the event source is not responsible for them -> treat exceptions happening as events
- catch block becomes an event source

Patterns:
- [[Observer pattern]]
