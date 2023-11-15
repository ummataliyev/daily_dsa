Data structure and algorithms are very important for getting a placement as it helps one to solve programming related problems and help us in cracking campus placements in no time.<br>

<img style="width:100%;" src="./static/image.jpg">

# Installation for Python

- 1 - clone repo https://github.com/Muhammadali-Akbarov/daily_dsa.git
- 2 - create a virtual environment and activate
- - `pip3 install virtualenv`
- - `virtualenv env` or `python -m venv env`
- - `env\Scripts\activate (windows)` or `source env/bin/activate (linux)`
- 3 -`cd into project "daily_dsa/python"`
- 4 - `pip install -r requirements.txt`
- 5 - `pylint python`
- 6 - `python tasks/main.py`


# Account to card implementation with Universal bank

Support Group - <a href="https://t.me/+Ng1axYLNyBAyYTRi">Telegram</a> <br/>


## Data Structures
- [Arrays (Lists in Python)](#arrays_in_python)
- [Tuples](#tuples_in_python)
- [CancelCheck](#cancelcheck)

# Methods

## arrays_in_python

```python
"""
arrays:
    in computer science, an array is a fixed-size,
    ordered collection of elements of the same data type,
    arrays have a fixed length, meaning that once you create
    an array with a specific size, you cannot change
    its size without creating a new array.

arrays in python:
    arrays in python are implemented as dynamic arrays,
    which means that their size can grow or shrink dynamically as elements
    are added or removed, python's built-in array module provides a way to
    create arrays of a specific data type, but most often, when people refer
    to "arrays" in Python, they are actually referring to "lists."

lists in python:
    in python, a list is a dynamic array that can contain elements of
    different data types, and it is one of the most commonly used data
    structures. lists are implemented as dynamic arrays,
    meaning that they can change in size as needed, lists are ordered collections of elements,
    they can contain elements of different data types and are mutable (modifiable).

how works with big O:
    big O notation is a way to describe the performance characteristics
    of algorithms or data structures, including lists (arrays or dynamic arrays),
    by analyzing how their performance scales with the size of the input data,
    when analyzing lists, you're typically concerned with operations like access,
    insertion, and deletion. here's how big O principles apply to lists:

    access (read/write) - O(1):
        in dynamic arrays (python lists),
        accessing elements by index is typically an O(1) operation,
        this means that regardless of the size of the list,
        the time it takes to access an element at a specific index remains constant.
        this is because dynamic arrays use contiguous memory locations,
        and simple arithmetic is used to calculate the memory address of the desired element.

    insertion at the end - O(1) (amortized):
        inserting an element at the end of a dynamic array is usually an O(1) operation on average,
        but it can become O(n) in some cases when the underlying array needs to be resized,
        however, dynamic arrays typically use amortization to minimize the frequency of resizing,
        making the average insertion at the end O(1).

    insertion at the beginning - O(n):
        inserting an element at the beginning of a dynamic array requires
        shifting all existing elements to make room for the new element,
        this operation is O(n), where n is the number of elements in the array,
        as it involves copying all elements to new memory locations.

    deletion - O(n):
        deleting an element in a dynamic array, except at the end,
        also requires shifting elements to close the gap created by the removal,
        this operation is O(n), similar to insertion at the beginning,
        because it involves copying elements.

    search - O(n):
        searching for an element in an unsorted dynamic array typically requires iterating through
        the array until the element is found or reaching the end. This is an O(n) operation because,
        in the worst case, you may need to examine all elements.
"""
import time
import unittest


class TestListInsertion(unittest.TestCase):
    """
    test list insertion.
    """
    def test_insert_element(self) -> None:
        """
        test insert element to list.
        if we want to insert an element in the list
        processor will execute shift operations.
        if my case shift operations will be executed 11 times (O(n)
        inserting an element at the beginning of a dynamic array)
        and insert operation will be executed 1 time.
        """
        my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]

        start_time = time.time_ns()

        my_list.insert(0, 12)

        end_time = time.time_ns()

        elapsed_time = end_time - start_time

        self.assertIn(
            member=12,
            container=my_list,
            msg="inserted element should be in the list"
        )

        self.assertEqual(
            first=len(my_list),
            second=12,
            msg="list length should increase by 1"
        )

        self.assertGreater(
            a=elapsed_time,
            b=-1,
            msg="elapsed time should be positive"
        )


if __name__ == '__main__':
    unittest.main()
```

## tuples_in_python

```python
"""
tuples in python:
    tuples in python are a versatile and useful data structure
    with several advanced features and use cases,
    here is some advanced information about tuples in python.

immutability tuples are immutable,
    meaning once you create a tuple, you cannot change its elements or size,
    this immutability makes tuples useful for situations
    where you want to ensure that the data remains constant.

features:
    tuple unpacking
    named tuples in collections module.
    slicing
    conversion
    arbitrary nesting
    hashability
"""
import unittest

from collections import namedtuple


class TestTuples(unittest.TestCase):
    """
    test the tuple features.
    """
    def test_tuple_unpacking(self) -> None:
        """
        test unpacking feature.
        """
        my_tuple = (1, 2, 3)

        a, b, c = my_tuple
        self.assertEqual(a, 1)
        self.assertEqual(b, 2)
        self.assertEqual(c, 3)

    def test_named_tuples(self) -> None:
        """
        test named tuples.
        """
        Point = namedtuple("Point", ["x", "y"])
        p = Point(3, 4)

        self.assertEqual(p.x, 3)
        self.assertEqual(p.y, 4)

    def test_slicing(self) -> None:
        """
        test slicing feature.
        """
        my_tuple = (1, 2, 3, 4, 5)

        subset = my_tuple[1:4]
        self.assertEqual(subset, (2, 3, 4))

    def test_conversion(self) -> None:
        """
        test conversion feature.
        """
        my_list = [1, 2, 3]

        my_tuple = tuple(my_list)
        self.assertEqual(my_tuple, (1, 2, 3))

    def test_arbitrary_nesting(self) -> None:
        """
        test arbitrary nesting feature.
        """
        nested_tuple = (1, (2, 3), (4, 5, (6, 7)))

        self.assertEqual(nested_tuple[1][0], 2)
        self.assertEqual(nested_tuple[2][2][1], 7)

    def test_hashability(self) -> None:
        """
        test hashability
        """
        my_dict = {(1, 2): "value"}

        self.assertEqual(my_dict[(1, 2)], "value")


if __name__ == '__main__':
    unittest.main()

```

## CancelCheck

```python
from pprint import pprint

from ubk.client import UniPosAPI
from ubk.types.request import RequestTransferCreditCancel


ubk_client = UniPosAPI(
    url="api-url",
    token="access-token"
)

resp_data = ubk_client.cancel_check(
    params=rpc_request.Cancel(
        ext_id="576d2529-5556-4ceb-b3ca-25cab475b57a"
    )
)

pprint(resp_data)

```