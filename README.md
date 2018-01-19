[![MATLAB FEX](https://img.shields.io/badge/MATLAB%20FEX-findduplicates-blue.svg)](https://mathworks.com/matlabcentral/fileexchange/57532-findduplicates) ![R2014b support](https://img.shields.io/badge/supports-R2014b%20and%20up-brightgreen.svg)

# `findduplicates`, find linear indices of duplicates in input

This function accepts the same input arguments as the [`unique`](http://mathworks.com/help/matlab/ref/unique.html) function, which is the basis for this function. `findduplicates` has two output arguments, `i1` and `i2`.

## Syntax

```MATLAB
[i1, i2] = FINDDUPLICATES(A)
[i1, i2] = FINDDUPLICATES(A, setOrder)
[i1, i2] = FINDDUPLICATES(A, occurence)
[i1, i2] = FINDDUPLICATES(A, __, 'rows')
[i1, i2] = FINDDUPLICATES(A, 'rows', __)
[i1, i2, C, ia, ic] = FINDDUPLICATES(__)

[i1, i2, C, ia, ic] = FINDDUPLICATES(A, 'legacy')
[i1, i2, C, ia, ic] = FINDDUPLICATES(A, 'rows', 'legacy')
[i1, i2, C, ia, ic] = FINDDUPLICATES(A, occurrence, 'legacy')
[i1, i2, C, ia, ic] = FINDDUPLICATES(A, 'rows', occurrence, 'legacy')
[i1, i2, C, ia, ic] = FINDDUPLICATES(A, occurrence, 'rows', 'legacy')
```

## Description

`[i1, i2] = findduplicates(A)` finds the linear indices of duplicates
in input `A`. The accepted input arguments are the same as accepted by
the `unique` function. The first output, `i1`, contains the linear indices
of the first duplicate elements into `A` that correspond to the
duplicates indexed by `i2`, the second output. `i1` may contain the same
index multiple times if an element exists more than twice in `A`. If no
duplicates exist, `i1` and `i2` are returned empty.

`[i1, i2] = findduplicates(A, setOrder)` supports the `'sorted'` (default)
or `'stable'` flags of the `unique` function, but have no effect to find
duplicates.

`[i1, i2] = findduplicates(A, occurence)` specifies which duplicate to
consider as the first, `occurence` can be `'first'` (default) or `'last'`.

`[i1, i2] = findduplicates(A, __, 'rows')` and `[i1, i2] = findduplicates(A, 'rows', __)`
treat each row of `A` as a single entity
and returns indices of duplicate rows. You must specify `A` and
optionally can specify `setOrder` or `occurence`. The `'rows'` option does
not support `cell` arrays.

`[i1, i2, C, ia, ic] = findduplicates(__)` also returns `C`, `ia` and `ic`
such that `[C, ia, ic] = unique(__)`. See the documentation for `unique`
for their meaning and use.

The syntaxes with the `'legacy'` option preserve the behaviour this
function would have on R2012b and prior releases. The `'legacy'` option
must be the last input argument. It does not support `categorical`
arrays, `datetime` arrays, `duration` arrays, tables or timetables.

## Examples

### Find first indices of duplicates and the other duplicates' indices:

```MATLAB
A = [9, 2, 9, 5]
[i1, i2] = findduplicates(A)
```

Result

```
A =
     9     2     9     5
i1 =
     1
i2 =
     3
```

This indicates that the first element in `A` has a duplicate at the
third element.

Run `findduplicatesdemo` for more examples of `findduplicates` based on
the examples of the `unique` function. See the contents of
findduplicatesdemo.m for details.

## Notes

 - `NaN` are considered as distinct values by the `unique` function, thus
 they are considered non-duplicates by `findduplicates` as well.

## Licence

GNU GPLv3
