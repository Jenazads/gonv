# Golang + Environment = gonv

gonv (Golang eNVironment) is a Golang implementation to manage environment variables in operating system.  
You can see an extended doc in [godocs](https://godoc.org/github.com/Jenazads/gonv).

Install it writing in terminal:

    go get github.com/jenazads/gonv

Example:

  ```go
    import(
      "fmt"
      "github.com/jenazads/gonv"
    )

    func main(){
      // using system environmental variables
      gonv.SetEnv("BOOL", true)
      isBool, _ := gonv.GetBoolEnv("BOOL")
      username, _:= gonv.GetEnv("USER") // return $USER system variable

      fmt.Println(username, ", ", isBool)
      
      gonv.SetEnv("NAME", "Jenazads")
      nameSystem ,_ := gonv.GetEnv("NAME")
      fmt.Println("name:", nameSystem)
      gonv.UpdateEnv("NAME", 4)
      nameUpdatedsystem, _ := gonv.GetIntEnv("NAME")
      fmt.Println("name updated:", nameUpdatedsystem)
      
      // using object environmental variables
      gonvObject := gonv.NewGonv()
      gonvObject.SetEnv("BOOL", true)
      isBool, _ = gonvObject.GetBoolEnv("BOOL")
      usernameObj,_ := gonvObject.GetEnv("USER") // return nil
      
      fmt.Println(usernameObj, ", ", isBool)
      
      gonvObject.SetEnv("NAME", "Jenazads")
      nameLocal, _ := gonvObject.GetEnv("NAME")
      fmt.Println("name:", nameLocal)
      fmt.Println(gonvObject)

      gonvObject.UpdateEnv("NAME", 4)
      nameLocal, _ = gonv.GetIntEnv("NAME") // we can set another type because is interface type !
      fmt.Println("name updated:", nameLocal)
      
      fmt.Println(gonvObject)
    }
  ```
