---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
footer: Distributed Systems Test Checklist
breaks: 'off'
---

# Distributed Systems Test Checklist

Test cases for retrieving data across a network

---

# Context

#### Architecture

- You have some **data on a server**
- There is an **API** or something to **fetch the data**
- You have some **UI** to **display the data**

---

# Context

#### Test Strategy

This checklist works whether you are 

- running unit tests against a test double representing your API
- running end to end tests against the real API
- manually testing against the real API

---

# Question

What do we test?

---

# Test 1: Show The Data

You get the data from the API and display it

---

# 8 Fallacies of Distributed Computing

#### Fallacy 1: The Nework Is Reliable

Sometimes we never hear back from the server

- Network error
- Server is handling too many other requests
- Another server our server depends on is unavailable
- Etc.

---

# Test 2: Unexpected Error

When the API does something it's not supposed to, what should users see?

- Bare minimum: don't blow up
- Maybe: show a message
- Maybe: allow retry
- Etc.

---

# 8 Fallacies of Distributed Computing

#### Fallacy 2: Latency Is Zero

Latency follows a distribution (imagine a bell curve)

- Often, our data loads "pretty quickly". 
- If it doesn't, a page refresh fixes it
    - because when we retry we're likely to hit the middle of the curve
- Users don't refresh when the site is weird

---

# Test 3: Loading State

While we're waiting for the API response, what do we see?

- Loading Spinner?
- Skeleton?
- Do we need a timeout where we give up?

---

# Test 1b: branching logic

When we show the data, are there multiple branches?

One test per branch

---

# Test 2b: additional errors

Are there any specific error scenarios that need special handling?

- Special messaging?
- Fallback behavior?


---

# Recap

1. Show The Data
    - Test 1b: branching logic
2. Test 2: Unexpected Error
    - Test 2b: additional errors
3. Test 3: Loading State
