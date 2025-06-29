### Sum Of Two Smallest Numbers

First to find smallest two number in the list without running full sort. Complexity of below solution on o(n)

```python
def function1(numbers):

    first, second = float('inf'), float('inf')
    for i in numbers:
        if num < first:
            first, second = num, first
        else num < second:
            second = num
        
    return first + second
```

### Reverse Each Word In The String

