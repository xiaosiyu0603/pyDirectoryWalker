# Readme
pyDirectoryWalker - A generator for traversing directories by Python 3.

本人英语水平低下，都用的简单词汇，应该很容易看懂。不然就用软件翻译一下吧。

### Usage

Use `dir_walker.walk(...)` to get the generator, which contains two overloads:

```python
@overload
def walk(path: Union[str, bytes], filter: Optional[Callable[[Union[str, bytes]], bool]] = None) -> Generator[Union[str, bytes], None, None]:
    ...

@overload
def walk(paths: Union[list[str], list[bytes]], filter: Optional[Callable[[Union[str, bytes]], bool]] = None) -> Generator[Union[str, bytes], None, None]:
    ...
```

The first argument is supposed to be a path-like array (e.g. `str` and `bytes`) or a list of path-like object. The second argument is supposed to be `None` or a `Callable` object (e.g. function), which shall returns `true` when the input path is needed.

A example is provided in code, follows `if __name__ == '__main__':`

```python
# form 'dir_walker.py'
# ...

if __name__ == '__main__':
    for path in walk(b".", lambda x: os.path.splitext(x)[1].lower() == b'.py'):
        print(repr(path))
```

The code will print all files under current folder and subfolder(s).

### Other

If you know a better implementation or find any bugs, please tell me by [issue](https://github.com/xiaosiyu0603/pyDirectoryWalker/issues). I will be very grateful.

