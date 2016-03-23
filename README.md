# SkyrimSaveReaderV2

#### Description

This is a new version of the program [Skyrim Save Reader] (https://github.com/navinparray/tesv-skyrim-save-reader "see other github repository") that attempts to solve the problem in a different way. The idea is to create a data structure that contains meta-data about the format of each field. The meta-data is used to read the data from the original save file.

In order to test this I'll create a valid data structure with properly formated data. The data will not be necessarily data that produces a valid save file but one that that conforms to the correct format.

#### Example Data Structure

Consider a structure as follows

```elixir
defmodule Structure.FunctionParam do
  @derive [Poison.Encoder]

  defstruct [
    [{
      field_name: 'param_name',
      field_size: 'little-unsigned-integer-size(16)',
      field_data: 0
    },
    {
      field_name: 'param_type',
      field_size: 'little-unsigned-integer-size(16)',
      field_data: 0      
    }
  ]

end
```

The program should take this structure and read two fields that are little-endian encoded unsigned integer with a size o two bytes.
