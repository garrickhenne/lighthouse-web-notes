# W03D04: Security and Real World HTTP Servers

- Storing passwords in plaintext is bad okay
- Hashing is a way to deal with storing passwords
- hash ⇒ one way function
- plaintext password ⇒ hashing algorithm (bcrypt) ⇒ hashed password (60 character string)
- salt → added to the plaintext password before hashing, adds some characters (salt) to password then put it through hashing algorithm
    - Ensures that common passwords arent recognizable as hashed passwords

### Plaintext cookies

- Also bad, technically worse than plaintext passwords
- encryption ⇒ two-way process (encrypted, decrypted)
- cookie-session middleware
- plaintext cookie → middleware → encrypted string
- browser sends encrypted cookie → middleware decrypts and gives decrypted cookie to server → server knows what the actual cookie

### HTTP vs HTTPS

- HTTP is vulnerable to man in the middle attack
- HTTPS encrypts calls
    - But you have to pay for it lol
- Asymmetric cryptography

### RESTful APIS

- Basically a naming convention
- instead of `GET /all-the-cars` or `POST /create-new-car`
- Should be less concise because it ends up actually giving us more detail (easier to follow)
- Browse `GET /cars`
- Read `GET /answers/:id`
- Edit `POST /answers`
- Add `POST /answers`
- Delete `POST /answers/:id/delete`

### Override HTTP Methods

- HTML only knows how to do `GET` and `POST` methods really.
- You can still make DELETE PATCH PUT methods using `POST`
- Its almost like syntactic sugar