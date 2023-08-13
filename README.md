# go-server
Writing the server code in Golang
---------------------------------

- Import Statements:

The main package is the entry point for the executable.
The fmt package is used for formatting and printing.
The log package provides logging functions.
The net/http package is used for creating HTTP servers and handling requests.

- Handler Functions:

formHandler: This function is called when the /form route is accessed. It handles a POST request that submits a form. It uses r.ParseForm() to parse the form data, and then it retrieves the values of the "name" and "address" fields using r.FormValue.
helloHandler: This function is called when the /hello route is accessed. It responds with "hello!" to a GET request to that route.

- Main Function:

The main function is where the server setup and configuration happen.
fileServer: A file server is created using http.FileServer. It serves static files from the "static" directory.
The / route is handled by the file server, serving static files.
The /form route is handled by the formHandler function.
The /hello route is handled by the helloHandler function.

- Starting the Server:

The server is started using http.ListenAndServe(":8080", nil). It listens on port 8080 and uses the default server configuration.

---------------------------------------------------------------------------------------------------------------------------------

- fmt Package:

fmt.Printf(format string, a ...interface{}): This function is used for formatted printing to the standard output (console). It accepts a format string and a variable number of arguments that match the placeholders in the format string.

- log Package:

log.Fatal(v ...interface{}): This function prints the provided arguments to the standard error (console) and then exits the program with a non-zero status code. It's typically used to report and terminate the program in case of an error.

- net/http Package:

http.ResponseWriter: This is an interface that represents the HTTP response. It's used to write the response data back to the client.

http.Request: This is a struct that represents an HTTP request received from a client.

http.Handle(pattern string, handler http.Handler): This function associates a given handler with a URL pattern. It's used to set up routing for different URLs.

http.HandleFunc(pattern string, handler func(http.ResponseWriter, *http.Request)): This function is similar to http.Handle, but it takes a function (handler) as an argument. It's a simpler way to define route handlers for simple use cases.

http.FileServer(root http.FileSystem): This function creates a new file server that serves files from the specified file system root (a directory). It returns an http.Handler that handles file requests.

http.Dir(dir string): This function creates an http.FileSystem interface from a given directory path. It's used to provide a file system root for the http.FileServer.

http.ListenAndServe(addr string, handler http.Handler): This function starts an HTTP server and listens on the provided address. The handler argument is an http.Handler that handles incoming requests. If nil is passed, the server uses the default serve mux (handler) provided by the package.

http.Error(w http.ResponseWriter, error string, code int): This function sends an HTTP error response to the client. It's used to return error responses with a specific status code and message.

http.StatusNotFound: This constant represents the HTTP status code 404 (Not Found).
