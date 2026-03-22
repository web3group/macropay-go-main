<!-- Start SDK Example Usage [usage] -->
```go
package main

import (
	"context"
	macropaygo "github.com/macrodeep/macropay-go"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := macropaygo.New(
		macropaygo.WithSecurity(os.Getenv("MACROPAY_ACCESS_TOKEN")),
	)

	res, err := s.Organizations.List(ctx, nil, macropaygo.Pointer[int64](1), macropaygo.Pointer[int64](10), nil)
	if err != nil {
		log.Fatal(err)
	}
	if res.ListResourceOrganization != nil {
		for {
			// handle items

			res, err = res.Next()

			if err != nil {
				// handle error
			}

			if res == nil {
				break
			}
		}
	}
}

```
<!-- End SDK Example Usage [usage] -->