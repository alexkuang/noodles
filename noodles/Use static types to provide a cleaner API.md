Let's say there is some function that registers a new user in the system and returns that user:

```scala
def registerUser(email: String, password: String): User
```

What happens when registration fails, e.g. the email is already taken or the password fails validation?  The only option is to throw an exception.  Issues: 
- Anyone calling `registerUser` has no idea about the possible error conditions unless they read through the entire implementation.
- Error handling then becomes overly broad (`log.error("something went wrong!")`) or entirely ad hoc.
- Even assuming all the right types exceptions are caught, there is potential for code drift if `registerUser` changes without corresponding updates to its callers.

This can be remedied with better use of types:

```scala
sealed trait RegistrationError
final case object EmailTaken extends RegistrationError
final case object InvalidEmail extends RegistrationError
final case object PasswordTooWeak extends RegistrationError

type RegistrationResult = Either<RegistrationError, User>

def registerUser(email: String, password: String): RegistrationResult
```

Now the API is much clearer at first glance, and the type-checker works to provide another layer of safety.

### Counterpoints
- The ergonomics here depend heavily on other language features.  For example, typescript's lack of support for pattern matching means that some [additional boilerplate](https://blog.logrocket.com/pattern-matching-and-type-safety-in-typescript-1da1231a2e34/) is needed for this approach.
- It's perfectly possible to write an API that is well-typed but difficult to use.  Types are not a silver bullet.
- Sometimes it's simpler to throw and error out.  e.g. `DatabaseIsDown` is probably not a `RegistrationError`: if the db is down, we probably want to just throw.