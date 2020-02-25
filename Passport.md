



## passport-local

### Install

```bash
$ npm install passport-local
```


### Usage

#### 1. Configure Strategy

아래의 Strategy는 **verify** callback 이 필요합니다. done을 통해 user를 리턴합니다.

```js
passport.use(new LocalStrategy(
  function(username, password, done) {
    User.findOne({ username: username }, function (err, user) {
      if (err) { return done(err); }
      if (!user) { return done(null, false); }
      if (!user.verifyPassword(password)) { return done(null, false); }
      return done(null, user);
    });
  }
));
```

#### 2. Authenticate Request

```js
app.post('/login', 
  passport.authenticate('local', { failureRedirect: '/login' }),
  function(req, res) {
    res.redirect('/');
  });
```


#### 3. 설명

어플리케이션이 app.post 를 호출하게 되면 passport.authenticate 이 호출된다. 이때 passport가 사용하는 strategy를 통해 user 오브젝트가 리턴되는데, 이 user 오브젝트는 req.user로 등록되어 활용된다.



#### 4. 세션

웹어플리케이션에서 인증을 통과하면 세션을 만들어서 정보를 저장한다.  
A session will be established and maintained via a cookie set in the user's browser.

```javascript
passport.serializeUser(function(user, done) {
  done(null, user.id);
});

passport.deserializeUser(function(id, done) {
  User.findById(id, function(err, user) {
    done(err, user);
  });
});
```

여기서 serializeUser는 세션에 user.id만을 저장하여 세션의 크키를 최소화 한다. 후속요청을 받게되면, 이 user ID가 사용자를 찾는데 사용되며, 이는 req.user에 저장된다. 위의 코드를 보면 User.findById 를 이용하는데, User는 어디 있는거지? 라는 의문이 든다. 

