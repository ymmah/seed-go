# Seed-Go
A Go client for the Seed API

[![GoDoc](http://img.shields.io/badge/go-documentation-blue.svg?style=flat-square)](http://godoc.org/github.com/seedco/seed-go)

## Usage

```go
// to obtain an access token go to https://api.seed.co/v1/public/auth/token in a browser and enter in your seed username/password

accessToken := "1.iap2H-4qQ-WR9sy55555uaytQ.o5A32LYL5-87a_60kcQiX1Lp878GVbx8xfVvTfp5tpc.orsHbAqao-5KfsH8SdglQFltK7Ii8ktL7xo8tls3HAB"

client := seed.New(accessToken)

getTransactionsReq := TransactionRequest{
	Client: client,
}

// create an iterator

iterator := getTransactionsReq.Iterator()

for iterator.HasNext() {
	var transactions []seed.Transaction
	var err error
	if transactions, _, err = iterator.Next(); err != nil {
		panic(err.Error())
	}
	fmt.Printf("Transactions:\n%v", transactions)
}

// previous will get the previous page of transactions

previousTransactions, _, err = iterator.Previous()
```
