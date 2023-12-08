# Using Sets in ABAP Program

In ABAP, a set is a logical grouping of values. Here's an example of how you can create a basic set and a unidimensional set, and also how to delete a set.

### Creating a Basic Set:

A basic set is a simple collection of values. In the example below, we'll create a basic set and add values to it.

```ABAP
DATA: basic_set TYPE TABLE OF rgsb4,
      set_name TYPE rgsb4-setname,
      value    TYPE rgsb4-value.

set_name = 'ZSET_BASIC'.

value = 'VALUE1'.
APPEND VALUE #( setname = set_name value = value ) TO basic_set.

value = 'VALUE2'.
APPEND VALUE #( setname = set_name value = value ) TO basic_set.

CALL FUNCTION 'S_SET_INSERT'
  EXPORTING
    setname = set_name
  TABLES
    values  = basic_set.

IF sy-subrc = 0.
  WRITE: / 'Basic Set created successfully.'.
ELSE.
  WRITE: / 'Error creating Basic Set.'.
ENDIF.
```

### Creating a Unidimensional Set:

A unidimensional set is similar to a basic set, but it can have multiple values for each entry.

```ABAP
DATA: unidimensional_set TYPE TABLE OF rgsb4,
      set_name           TYPE rgsb4-setname,
      value              TYPE rgsb4-value,
      id                 TYPE rgsb4-id.

set_name = 'ZSET_UNIDIMENSIONAL'.

value = 'VALUE1'.
id = 'ID1'.
APPEND VALUE #( setname = set_name id = id value = value ) TO unidimensional_set.

value = 'VALUE2'.
id = 'ID2'.
APPEND VALUE #( setname = set_name id = id value = value ) TO unidimensional_set.

CALL FUNCTION 'S_SET_INSERT'
  EXPORTING
    setname = set_name
  TABLES
    values  = unidimensional_set.

IF sy-subrc = 0.
  WRITE: / 'Unidimensional Set created successfully.'.
ELSE.
  WRITE: / 'Error creating Unidimensional Set.'.
ENDIF.
```

### Deleting a Set:

To delete a set, you can use the `S_SET_DELETE` function module.

```ABAP
DATA: set_name TYPE rgsb4-setname.

set_name = 'ZSET_BASIC'. "Replace with your set name.

CALL FUNCTION 'S_SET_DELETE'
  EXPORTING
    setname = set_name.

IF sy-subrc = 0.
  WRITE: / 'Set deleted successfully.'.
ELSE.
  WRITE: / 'Error deleting set.'.
ENDIF.
```

Make sure to replace the set names ('ZSET_BASIC', 'ZSET_UNIDIMENSIONAL') with the names you want to use. Also, handle errors appropriately based on your application's requirements.
