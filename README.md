## Assignment: Caching the Inverse of a Matrix
## This function creates a special "matrix" object that can cache its inverse


      makeCacheMatrix <- function(x = matrix()) {
          ##store the cache value, initialize to NULL
          inv <- NULL
      
          ##create a matrix
          set <- function(y) {
               x <<- y
                inv <<- NULL
          }
      
          ##get the value of the matrix
          get <- function() x
      
          ##invert the matrix and store in cache
          setinverse <- function(inverse) inv <<- inverse
      
           ##get the inverted matrix
          getinverse <- function() inv
      
          ##return the created function
          list(set=set, get=get, setinverse=setinverse, getinverse=getinverse)
    }


##This function computes the inverse of the special "matrix" returned
##by makeCacheMatrix above

    cacheSolve <- function(x, ...) {
         ##get the inverted matrix from cache
          inv <- x$getinverse()
      
          ##return inverted matrix in cache
          if(!is.null(inv)) {
                message("getting cached data.")
                return(inv)
          }
          data <- x$get()
      
          ##computing the inverse of a square matrix
          inv <- solve(data, ...)
          x$setinverse(inv)
          inv
    }

    ##TESTING
    ## a <- makeCacheMatrix(matrix(1:4, nrow=2, ncol=2))
    ## a$get()
    ## [,1] [,2]
    ## [1,]    1    3
    ## [2,]    2    4
    ## a$getinverse()
    ## NULL
    ## cacheSolve(a)
    ## [,1] [,2]
    ## [1,]   -2  1.5
    ## [2,]    1 -0.5


