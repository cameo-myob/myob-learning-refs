# Testing isn't fun

## Unit Testing Goals
- Thorough - prove that the single object under test is behaving correctly
- Stable - they shouldn't break when you change something
- Fast
- Few - no extra lines of code to maintain

### Message origins for object
- Incoming messages
- Outgoing messages
- Sent to self

Messages can be queries or commands. Queries have no side effects - return something and change nothing. Commands return nothing but change something.

## Rules
Message | Query | Command
--- | --- | ---
Incoming | Test incoming query messages by making assertions about what they send back. Test the interface, not the implementation. | Test incoming command messages by making assertions about direct public side effects |
Sent to Self | Ignore them | Ignore them |  
Outgoing | Same rule as 'sent to self' - outgoing queries on an object are incoming queries on another object | Expect to send outgoing command messages |

### DRY it out
Receiver of the incoming message has the sole responsibility for asserting the result of direct public side effects

## Sent to self messages
Don't test private methods
Don't make assertions about their result
Don't expect to send them
Caveat - break rule if it saves money during development

If the message has no visible side-effects, it is invisible to the rest of your app and the sender should not test it.