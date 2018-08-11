# Travis Cheatsheet

- Activate your repo on travis-ci.com 
- Setup a `.travis.yml` file in your project root (Travis only runs builds on the commits you push after you’ve added a .travis.yml file)

### Select a language in your `.travis.yml`
[see the full list of supported languages](https://docs.travis-ci.com/user/languages/)

e.g.

```
language: ruby
language: java
language: node_js
language: python
language: php
```

### Get database  (default user is `postgres` with a blank password)
```
services:
  - postgresql

before_script:
  - psql -c 'create database travis_ci_test;' -U postgres
```

### Set environment variables

Need a private variable? Navigate to the repository in question, choose “Settings” from the cog menu, and click on “Add new variable” in the “Environment Variables” section.

```
env:
  - FOO=bar
```

### Deploy after a successful build 

```
deploy:
  provider: heroku
  api_key:
    secure: "YOUR ENCRYPTED API KEY"
```

### Run CodeCov (Istanbul used as example to generate lcov)
```
script:
  - istanbul cover test.js
after_success:
  - bash <(curl -s https://codecov.io/bash)
```

### Send a webhook notification

```
notifications:
  webhooks: http://your-domain.com/notifications
```

### Configure e-mail notifications
```
notifications:
  email:
    recipients:
      - one@example.com
      - other@example.com
    on_success: never # default: change
    on_failure: always # default: always
```
```
notifications:
  email: false
```
