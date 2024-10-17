                                     RESTFULL API METHODS:

GET (in this method we send not the data but get the data).
POST (in this method we send the data then get the data ).
DELETE (in this method we can delete the data).
PATCH (in this method we can change just image).
PUT (in this method whole object can be changed).

                                   Real Application like Facebook:

now in this application we check the all methods of Restfull Api.

                                   GET Example:
In a Facebook-like application, this could be fetching a user’s profile or a list of posts.
Calling GET multiple times results in the same data being fetched without side effects.

app.get('/users', (req, res) => {
  res.json(users); 
});

 Get a user by ID (fetch a specific profile)
app.get('/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');
  res.json(user);
});

                                   POST Example:
Creating a new user account.
Posting a new status or photo.

app.use(express.json());

 Create a new user (register a new profile)
app.post('/users', (req, res) => {
  const newUser = {
    id: users.length + 1,
    name: req.body.name
  };
  users.push(newUser); 
  res.status(201).json(newUser);
});

                                    PUT Example:

Updating user profile information like changing username, or email.
Editing an already posted status.

app.put('/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');

  user.name = req.body.name; 
  res.json(user); 
});

                                    DELETE Example:

Deleting a user account.
Removing a post or comment.

app.delete('/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');
  users = users.filter(u => u.id !== parseInt(req.params.id));
  res.json({ message: 'User deleted' }); 
});

                                  PATCH Example:

Updating just the profile picture or username of a user, without affecting other parts of the profile.

app.patch('/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found');
  if (req.body.name) {
    user.name = req.body.name; 
  }
  if (req.body.email) {
    user.email = req.body.email; 
  }

  res.json(user); 
});
