# ==============================================================================
# Stage: build
# ==============================================================================
# Use the golang image as a base
FROM golang:1.25 AS build

# Set working directory to src/
WORKDIR /src

# Copy a simple Go program to main.go
COPY <<EOF ./main.go
package main

import "fmt"

func main() {
  fmt.Println("hello, world")
}
EOF

# Compile main.go into a binary at /bin/hello
RUN go build -o /bin/hello ./main.go


# ==============================================================================
# Stage: main
# ==============================================================================
FROM scratch

COPY --from=build /bin/hello /bin/hello

CMD ["/bin/hello"]