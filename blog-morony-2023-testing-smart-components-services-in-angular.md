[[$Blogs]]

https://modernangular.com/articles/testing-smart-components-services-in-angular

Smart components supply dumb ones with input, this needs to be tested. They also react to outputs emitting from dumb components, which should be tested. Also the input is often gathered from sources from services.

Often, the tests for the smart components are very similar to the dumb ones, with just a few things moved around.

Do not actually test the service, use mocks.
