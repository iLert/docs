---
description: >-
  Our open source client is available under MIT and Apache 2.0 License. It is
  also the backend of our Terraform provider.
---

# Go Client

You can find the official iLert Go client on our Github organization: [https://github.com/iLert/ilert-go](https://github.com/iLert/ilert-go)

Install as usual via `import ("github.com/iLert/ilert-go")`

```go
package main

import (
	"fmt"
	"log"
	"github.com/iLert/ilert-go"
)

func main() {

	var org = "your organization"
	var username = "your username"
	var password = "your password"	
	client := ilert.NewClient(ilert.WithBasicAuth(org, username, password))
	
	result, err := client.GetAlertSources(&ilert.GetAlertSourcesInput{})
	if err != nil {
		log.Println(result)
		log.Fatalln("ERROR:", err)
	}
	
	log.Println(fmt.Sprintf("Found %d alert sources\n\n ", len(result.AlertSources)))
	for _, alertSource := range result.AlertSources {
		log.Println(fmt.Sprintf("%+v\n", *alertSource))
	}
}
```

Please feel free to [reach out to us](../../contact.md) with a Github issue in case you need help or have feature requests.[  
](https://docs.ilert.com/rest-api/client-libraries)  


