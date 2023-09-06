Topics
- unit test frameworks

----

# Mocking Objects
- mock objects have no functionality
	- has all the same methods and datatypes
- Stubbing - when test code supplies its test input
## Java - Mockito
Making new mock objects
```java
Controller contr = mock(Controller.class); // Note the .class
EmailSender email = mock(EmailSender.class);
```

Setting the return values of mock objects to fake problem
``` java
when(contr.problemExists()).thenReturn(true);
when(contr.getMessage()).thenReturn("Test msg");
```
- `when()` and `thenReturn()` are part of Mockito

Checking if method was called
``` java
//if send() was called with imports, nothing happens. otherwise test fails
verify(email).send("stat@xyz.com", "Test msg");

//asserts send() was called zero times (argument import does not matter)
verify(email, times(0)).send(anyString(), anyString());
```
- `verify` is like the `assert` of Mockito

## Python - unittest.mock
Making new mock objects
```python
# Python
contr = Mock()
email = Mock()
```

Setting return values of mock objects
``` python
# Note: We are NOT calling the method!!!
contr.problemExists = Mock(return_value=True)
contr.getMessage = Mock(return_value="Test msg")
```

Checking if method was called
``` python
email.send.assert_called_with("stat@xyz.com", "Test msg")
email.send.assert_not_called()
```

