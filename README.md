# sarvam_assignment

## Rearrange Tensor Function

This repository contains a Python implementation of a `rearrange` function that reshapes tensors based on a given pattern. The function parses the pattern and rearranges the axes of the tensor accordingly.

### Approach and Design Decisions

#### Parsing the Pattern:
The `parse_pattern` function splits the input pattern into two parts: **input** and **output**.

- It processes each part of the pattern by checking for spaces and parentheses, allowing support for both individual axes and merged axes (e.g., `(h w)`).

#### Rearranging the Tensor:
The `rearrange` function maps the axes of the input tensor to the output pattern.

- It handles cases like **transposition**, **splitting/merging axes**, and **reshaping**.
- For merged axes, the sizes of individual axes are combined into one dimension.
- It also handles **ellipsis (`...`)** for batch dimensions, preserving the batch shape while rearranging the other dimensions.

### Key Features:
- **Transposition**: Swapping axes (e.g., from `'h w -> w h'`).
- **Splitting Axes**: Splitting a merged axis back into individual axes (e.g., `(h w) c -> h w c`).
- **Merging Axes**: Combining multiple axes into a single axis (e.g., `'a b c -> (a b) c'`).
- **Repeating Axes**: Expanding a singleton axis to a new size (e.g., `'a 1 c -> a b c'`).
- **Ellipsis Handling**: Managing batch dimensions with ellipsis (`...`), ensuring batch dimensions are preserved during rearrangement.

### Error Handling:
- The function checks for mismatches in tensor shape and pattern consistency.
- It raises errors if the pattern cannot be applied to the tensor shape, ensuring that the dimensions align.

---
