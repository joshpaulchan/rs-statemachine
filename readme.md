# statemachine

`statemachine` is my implementation of a generic statemachine library, that I'm using to learn Rust.

## Usage

Run: `cargo run`
Test: `cargo test`


## Design

I wanted to design a generic statemachine that I can use to model discrete systems, like:

1. Turn-based games
1. Light switches / simple controls

and I also wanted to learn Rust. So this here is it!

In pseudo code, what I want to implement is something akin to:

```java
interface StateMachine<State, Event> {
  void? bool? Result? Future<State>? dispatch( Event ) // dispatch an event that may trigger a transition
	// wonder if there should be some way to rehydrate the state machine...? getDispatches()?
  StateMachine addHandler( EventHandler ) // add a listener and only trigger on certain state transitions?

  State getState() // introspect current state
  getStates() // introspect last n states? all states?
}

interface EventHandler {
  Validator<AbstractState, AbstractEvent> preconditionValidator;
  BiFunction<CurrentState, Event, NexState> stateGenerator; // should state be here...?
  Consumer<Transition> sideEffectOnTransition;
}

class Transition { // passed to listen?
  AbstractState previousState;
  Event event;
  AbstractState currentState;
}
```
