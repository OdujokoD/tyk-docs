---
date: 2017-03-27T17:29:00+01:00
title: “Key object validation failed“ error when updating a key
menu:
  main:
    parent: "Tyk Gateway"
weight: 5 
---

### Description
Users receive this error message when attempting to make API calls to an existing key.

### Cause
When the token was created, most probably it was configured without the meta_data key.

### Solution
The user will need to add the key-value pair meta_data: {} to their key as per the [documentation][1].

[1]: /docs/tyk-rest-api/token-management/
