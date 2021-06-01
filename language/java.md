# java notes

## Comparable<T>

- interface
- implemented by entity
- `compareTo(obj a)`

## Comparator<T>

- interface
- implemented by comparator
- `compare(obj a,obj b)`

## arraycopy

- copy 1d array

## final variable

- holding constant reference (address)
- does not affect modification in the referenced object
- ensuring pointing same object but not same value
  - instead, making defensive copy of object if needed

## StringBuffer

- use StringBuffer to modify string when it would be made frequently or involve variable wi uncertain value
- `append()`
- `toString()`
