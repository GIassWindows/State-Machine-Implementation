# State Machine Implementation
Just another state machine implementation.
Also uses my signal implementation.

## Documentation

```lua
local CustomStates = {
    Test = {
        "Test1"
    },
    Test1 = {
        ""
    }
}

local StateMachine = require("../Path/To/StateMachine.luau");
local States = StateMachine.Create(CustomStates);

States:Enter("Test"); -- Enters the state "Test".
States:Enter("Test1"); -- Does nothing, Test1 is a state that's untransitionable.

States:Exit("Test"); -- Exits the state "Test".

-- Callback parameter is the state you entered to.
States.OnStateEntered:Connect(function(StateEntered: string)
    print(StateEntered); -- output: "Test";
end)

-- Callback parameter is the state you exited from.
States.OnStateExited:Connect(function(OnStateExited: string)
    print(OnStateExited); -- output: "Test";

    States:Enter("Test1"); -- Enters the state "Test1" because it is no longer in state Test.
end)
