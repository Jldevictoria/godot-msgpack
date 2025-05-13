
# godot-msgpack

(Originally created by xtpor - Tintin Ho 2019)

A MessagePack serializer implemented in pure GDScript

- No dependency
- No native binding required

# Installation

Copy the `msgpack.gd` at the root of the repository into your godot project

# Usage

```gdscript
var Msgpack = preload("res://msgpack.gd")

func _myfunc():
    var data = {"type": "wizard", "attack": 10, "weapon": ["dagger", "staff"]}

    var res = Msgpack.encode(data)
    print(res.result) # A PackedByteArray of the data encoded MessagePack

    var res2 = Msgpack.decode(res.result)
    print(res2.result) # Get back the original data
```

## class `Msgpack`

### `static Dictionary encode(Variant value)`

Convert a value (number, string, array and dictionary) into their
counterparts in messagepack. Returns dictionary with three fields:
`result` which is the packed data (a PackedByteArray); `error` which is the
error code; and `error_string` which is a human readable error message

### `static Dictionary decode(PackedByteArray bytes)`

Convert a packed data (a PackedByteArray) back into a value, the reverse of the
encode function. The return value is similar to the one in the encode
method

# Limitation

- Only support null, boolean, integer, float, PackedByteArray, string, array and
  dictionary. No support for other data type like Vector2 and Vector3
- No support for the ext datatype in MessagePack
- Slow compare to the built-in binary serialization in godot

# Testcases

```
godot -s run_test.gd
```
