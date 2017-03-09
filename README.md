# cypress-bumpercar

Make it easy to bump versions and re-run CI builds across many projects and CI providers.

```coffeescript
# configure a new Bumpercar
car = bumpercar.create({
  providers: {
    travis: {
      # find/create one here: https://github.com/settings/tokens
      githubToken: "github-token-for-user-with-repo-privileges"
    }
    circle: {
      # find/create one here: https://circleci.com/account/api
      circleToken: "circle-token-for-user-with-project-privileges"
    }
  }
})

# bump your ENV vars with ease
car.updateProjectEnv("cypress-io/cypress-download", "circle", {
  VAR_1: "lo"
  VAR_2: "and"
  VAR_3: "behold"
})

.then ->
  # kick off a new build/run with your new vars
  car.runProject("cypress-io/cypress-download", "circle")
```
