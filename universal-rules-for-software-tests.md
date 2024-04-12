Tests should be kept as short and concise as possible.

Tests should run as fast as possible. If it's taking too long to run your tests, split them up and run them in parallell. Only run the tests strictly needed for the given step in the deployment pipeline, e.g. don't run all your acceptance tests as one of the first things (unless for some reason you really have to.).