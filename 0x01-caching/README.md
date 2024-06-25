# 0x01. Caching

## Background Context
In this project, you will learn about different caching algorithms.

## Resources
To get a better understanding of the concepts covered in this project, you should read or watch the following resources:
- [Cache replacement policies - FIFO](https://en.wikipedia.org/wiki/Cache_replacement_policies#First_In_First_Out)
- [Cache replacement policies - LIFO](https://en.wikipedia.org/wiki/Cache_replacement_policies#Last_In_First_Out)
- [Cache replacement policies - LRU](https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_Recently_Used)
- [Cache replacement policies - MRU](https://en.wikipedia.org/wiki/Cache_replacement_policies#Most_Recently_Used)
- [Cache replacement policies - LFU](https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_Frequently_Used)

## Learning Objectives
By the end of this project, you should be able to explain the following concepts to anyone, without needing to refer to Google:
- What caching is and why it is useful
- Different types of cache replacement policies: FIFO, LIFO, LRU, MRU, LFU
- How to implement caching algorithms in Python

## BaseCaching
All your classes must inherit from the BaseCaching class, which is defined as follows:


#!/usr/bin/python3
""" BaseCaching module
"""

class BaseCaching():
    """ BaseCaching defines:
      - constants of your caching system
      - where your data are stored (in a dictionary)
    """
    MAX_ITEMS = 4

    def __init__(self):
        """ Initialize
        """
        self.cache_data = {}

    def print_cache(self):
        """ Print the cache
        """
        print("Current cache:")
        for key in sorted(self.cache_data.keys()):
            print("{}: {}".format(key, self.cache_data.get(key)))

    def put(self, key, item):
        """ Add an item in the cache
        """
        raise NotImplementedError("put must be implemented in your cache class")

    def get(self, key):
        """ Get an item by key
        """
        raise NotImplementedError("get must be implemented in your cache class")
# Tasks

## 0. Basic Dictionary
Create a class `BasicCache` that inherits from `BaseCaching` and implements a basic caching system:

- You must use `self.cache_data` - a dictionary from the parent class `BaseCaching`.
- This caching system doesn't have a limit.

### Methods
- `put(self, key, item)`:
  - Assign the item value to the key in `self.cache_data`.
  - If key or item is None, this method should not do anything.
- `get(self, key)`:
  - Return the value in `self.cache_data` linked to key.
  - If key is None or if the key doesn't exist in `self.cache_data`, return None.

## 1. FIFO Caching
Create a class `FIFOCache` that inherits from `BaseCaching` and implements a caching system with FIFO replacement policy:

- You must use `self.cache_data` - a dictionary from the parent class `BaseCaching`.
- You can overload the `__init__` method, but don't forget to call the parent `__init__`: `super().__init__()`

### Methods
- `put(self, key, item)`:
  - Assign the item value to the key in `self.cache_data`.
  - If key or item is None, this method should not do anything.
  - If the number of items in `self.cache_data` is greater than `BaseCaching.MAX_ITEMS`:
    - Discard the first item put in cache (FIFO algorithm).
    - Print `DISCARD:` followed by the discarded key and a new line.
- `get(self, key)`:
  - Return the value in `self.cache_data` linked to key.
  - If key is None or if the key doesn't exist in `self.cache_data`, return None.

## 2. LIFO Caching
Create a class `LIFOCache` that inherits from `BaseCaching` and implements a caching system with LIFO replacement policy:

- You must use `self.cache_data` - a dictionary from the parent class `BaseCaching`.
- You can overload the `__init__` method, but don't forget to call the parent `__init__`: `super().__init__()`

### Methods
- `put(self, key, item)`:
  - Assign the item value to the key in `self.cache_data`.
  - If key or item is None, this method should not do anything.
  - If the number of items in `self.cache_data` is greater than `BaseCaching.MAX_ITEMS`:
    - Discard the last item put in cache (LIFO algorithm).
    - Print `DISCARD:` followed by the discarded key and a new line.
- `get(self, key)`:
  - Return the value in `self.cache_data` linked to key.
  - If key is None or if the key doesn't exist in `self.cache_data`, return None.

## 3. LRU Caching
Create a class `LRUCache` that inherits from `BaseCaching` and implements a caching system with LRU replacement policy:

- You must use `self.cache_data` - a dictionary from the parent class `BaseCaching`.
- You can overload the `__init__` method, but don't forget to call the parent `__init__`: `super().__init__()`

### Methods
- `put(self, key, item)`:
  - Assign the item value to the key in `self.cache_data`.
  - If key or item is None, this method should not do anything.
  - If the number of items in `self.cache_data` is greater than `BaseCaching.MAX_ITEMS`:
    - Discard the least recently used item (LRU algorithm).
    - Print `DISCARD:` followed by the discarded key and a new line.
- `get(self, key)`:
  - Return the value in `self.cache_data` linked to key.
  - If key is None or if the key doesn't exist in `self.cache_data`, return None.

## 4. MRU Caching
Create a class `MRUCache` that inherits from `BaseCaching` and implements a caching system with MRU replacement policy:

- You must use `self.cache_data` - a dictionary from the parent class `BaseCaching`.
- You can overload the `__init__` method, but don't forget to call the parent `__init__`: `super().__init__()`

### Methods
- `put(self, key, item)`:
  - Assign the item value to the key in `self.cache_data`.
  - If key or item is None, this method should not do anything.
  - If the number of items in `self.cache_data` is greater than `BaseCaching.MAX_ITEMS`:
    - Discard the most recently used item (MRU algorithm).
    - Print `DISCARD:` followed by the discarded key and a new line.
- `get(self, key)`:
  - Return the value in `self.cache_data` linked to key.
  - If key is None or if the key doesn't exist in `self.cache_data`, return None.

## 5. LFU Caching
Create a class `LFUCache` that inherits from `BaseCaching` and implements a caching system with LFU replacement policy:

- You must use `self.cache_data` - a dictionary from the parent class `BaseCaching`.
- You can overload the `__init__` method, but don't forget to call the parent `__init__`: `super().__init__()`

### Methods
- `put(self, key, item)`:
  - Assign the item value to the key in `self.cache_data`.
  - If key or item is None, this method should not do anything.
  - If the number of items in `self.cache_data` is greater than `BaseCaching.MAX_ITEMS`:
    - Discard the least frequently used item (LFU algorithm).
    - If there are multiple items with the same frequency, use the LRU algorithm to discard the least recently used among them.
    - Print `DISCARD:` followed by the discarded key and a new line.
- `get(self, key)`:
  - Return the value in `self.cache_data` linked to key.
  - If key is None or if the key doesn't exist in `self.cache_data`, return None.

