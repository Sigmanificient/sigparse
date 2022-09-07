# sigparse

Backports python3.10 typing features into python3.8 and 3.9.

## Example

```python
import sigparse

def func(param_a: list[str], param_b: str | int, param_c: tuple[int | None]):
    ...

# This returns the same result in python 3.8, 3.9, and 3.10!
sigparse.sigparse(func)
```

## Notes
### Inspect

This module uses inspect behind the scenes. For that reason:

- `sigparse.Parameter.default` is `inspect._empty` when there is no default value.
- `sigparse.Parameter.kind` is `inspect._ParameterKind`.


### Annotated
`typing.Annotated` will always be evaluated with `include_extras=True` in python3.9. This ensures that
`typing.Annotated` will be parsed the same in all python versions.
