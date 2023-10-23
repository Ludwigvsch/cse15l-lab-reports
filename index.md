## Part 1

![Screenshot 2023-10-22 at 9 47 45 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/2c976eca-2ca8-4c5e-a1fc-25846772f3b1)

![Screenshot 2023-10-22 at 9 49 06 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/f992203d-9776-48ee-b486-ce6129b24d3e)

![Screenshot 2023-10-22 at 9 49 53 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/d20956a0-d2eb-4693-8900-5806f737b489)

**First Screenshot:**
**User Input:** 1. Hello, how are you?

**Method Called:** `handleRequest(URI url)`

**Relevant Arguments:** URI url with a path of `/add-message` and a query of `s=Hello, how are you?`.

**Relevant Field Values Before Method Call:**

`str = ""`

`number = 0`

**Field Value Changes:**

str changes to `"1. Hello, how are you?\n"`

number increments to 1

**Second Screenshot:**

**User Input:** 1. Hello, how are you?

**User Input:** 2. Hi, I am good. How are you?

**Method Called:** `handleRequest(URI url)`

**Relevant Arguments:** URI url with a path of `/add-message` and a query of `s=Hi, I am good. How are you?.`

**Relevant Field Values Before Method Call:**

`str = "1. Hello, how are you?\n"`

`number = 1`

**Field Value Changes:**

str changes to "1. Hello, how are you?\n2. Hi, I am good. How are you?\n"

number increments to 2

In both cases, the `handleRequest` method is invoked with the URI containing the `/add-message` path and respective query strings. The fields `str` and `number` are updated accordingly with each request, appending the new message to `str` and incrementing number by 1. This is achieved through the logic in the `handleRequest` method, which checks the URI path and query parameters to handle the request appropriately.

These steps demonstrate how my StringServer and Handler class work together to process and respond to incoming requests, with particular emphasis on the `/add-message` path.

## Part 2

**Path to the public key:**

![Screenshot 2023-10-22 at 10 11 16 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/080aa0e6-9fd9-4c34-b5f6-f3342074fa9b)


**Path to the private key:**

![Screenshot 2023-10-22 at 10 07 01 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/57a8465d-fe56-4b83-b9a4-14be4a9fd8ba)

**Logging into ieng6 without having to type in password**
![Screenshot 2023-10-22 at 10 13 17 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/479a6c91-e16d-4475-85cf-0be1148db9b8)

## Part 3

Since I already knew how to interact with remote servers and how ssh works, the only new thing I learned is how to add the private key to my own files so that I do not always have to type in the password when trying to log into the system. Besides that I learned a little bit more about URIs and how to interact with them in java. I also learned some basics about java that I didn't know about before like how to set up a Server.
