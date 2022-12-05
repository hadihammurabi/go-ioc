# moved to https://github.com/gowok/ioc

# go-ioc
IOC addons for Go

# Example
```go
package main

import (
  "fmt"
  "github.com/hadihammurabi/go-ioc/ioc"
)

type UserRepository struct {}
type ProfileRepository struct {}

func (repo *UserRepository) FindAll() {}

type UserService struct {
  UserRepo *UserRepository        `ioc:"inject"`
  ProfileRepo *ProfileRepository  `ioc:"inject"`
}

func main() {
  ioc.Set(func() UserRepository { return UserRepository{} })
  ioc.Set(func() ProfileRepository { return ProfileRepository{} })

  userService := UserService{
    UserRepo: &UserRepository{},
    ProfileRepo: &ProfileRepository{},
  }

  ioc.Inject(userService)

  userService.UserRepo.FindAll()
}
```

See full example [here](https://gistery.com/go-ioc-example-uc3q3a0p).
