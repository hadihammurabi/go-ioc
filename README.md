# go-ioc
IOC addons for Go

# Example
```go
package main

import (
  "fmt"
  "github.com/hadihammurabi/go-ioc/ioc"
)

func main() {
  ioc.Set(func() UserRepository { return UserRepository{} })
  ioc.Set(func() ProfileRepository { return ProfileRepository{} })
  
  userService := UserService{
    UserRepo: &UserRepository{},
    ProfileRepo: &ProfileRepository{},
  }

  ioc.Inject(userService)
  
  userService.UserRepo.findAll()
}
```
