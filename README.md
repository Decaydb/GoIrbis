# GoIrbis

ManagedIrbis ported to Go language

Currently supported Go 1.12 on 64-bit Windows and Linux

### Build status

[![Build status](https://img.shields.io/appveyor/ci/AlexeyMironov/goirbis.svg)](https://ci.appveyor.com/project/AlexeyMironov/goirbis/)
[![Build status](https://api.travis-ci.org/amironov73/GoIrbis.svg)](https://travis-ci.org/amironov73/GoIrbis/)

### Sample program

```go
package main

import "./src/irbis"

func main ()  {
	// Connect to the server
	connection := irbis.NewConnection()
	connection.Host = "localhost"
	connection.Username = "librarian"
	connection.Password = "secret"
	if !connection.Connect() {
		println("Can't connect")
		connection.FailOnError()
	}

	// Will be disconnected at exit
	defer connection.Disconnect()

	// General server information
	println("Server version:", connection.ServerVersion)
	println("Interval:", connection.Interval)

	// Proposed client settings from INI-file
	ini := connection.Ini
	dbnnamecat := ini.GetValue("Main", "DBNNAMECAT", "???")
	println("DBNNAMECAT:", dbnnamecat)

	// Search for books written by Byron
	found := connection.Search("\"A=Byron, George$\"")
	println("Records found:", len(found))

	for _, mfn := range found {
		// Read the record
		record := connection.ReadRecord(mfn)

		// Get field/subfield value
		title := record.FSM(200, 'a')
		println("Title:", title)

		// Formatting (at the server)
		description := connection.FormatMfn("@brief", mfn)
		println("Description:", description)
	}
}
```

#### Documentation (in russian)

[![Badge](https://readthedocs.org/projects/goirbis/badge/)](https://goirbis.readthedocs.io/)
