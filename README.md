# SimpleHttp
A HTTP/1.1 polling server with thread pooling, using only Linux system API and C++.

# Performance
Used i5 for server and client (2.5GHzx4), that communicates over school intranet.
1. Multithreading without polling @ 031bec.  
Avg time to serve 10k request: 11.189ms
2. Polling @ master branch.  
Avg time to serve 10k request: 12.772ms
3. Polling with threadpool @ feature/threadpool branch.  
Avg time to serve 10k request: 12.090ms

All using the benchmark script in master branch. Threadpool does not perform well on this benchmark because most of the time, only one worker thread is enough to handle the requests. We need better benchmarking script that sends requests at a higher speed in this case.

NOTE: Polling server is CPU intensive because it is running infinite loop in multiple threads, waiting for a job to be assigned. To properly benchmark the server, you need to use 2 different machines for client and server.

## How to run
`$ make test`  
`$ ./http_server`

## Supported methods
`GET` and `HEAD`. All other methods are optional for general-purpose servers according to RFC7231.

## Future works
- Support other methods and additional headers
- Provide better benchmarking tool
