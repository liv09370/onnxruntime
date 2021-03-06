## 0.5.2 (unreleased)

- Fixed error with `execution_mode` option

## 0.5.1 (2020-11-01)

- Updated ONNX Runtime to 1.5.2
- Added support for string output
- Added `output_type` option
- Improved performance for Numo array inputs

## 0.5.0 (2020-10-01)

- Updated ONNX Runtime to 1.5.1
- OpenMP is now required on Mac
- Fixed `mul_1.onnx` example

## 0.4.0 (2020-07-20)

- Updated ONNX Runtime to 1.4.0
- Added `providers` method
- Fixed errors on Windows

## 0.3.3 (2020-06-17)

- Fixed segmentation fault on exit on Linux

## 0.3.2 (2020-06-16)

- Fixed error with FFI 1.13.0+
- Added friendly graph optimization levels

## 0.3.1 (2020-05-18)

- Updated ONNX Runtime to 1.3.0
- Added `custom_metadata_map` to model metadata

## 0.3.0 (2020-03-11)

- Updated ONNX Runtime to 1.2.0
- Added model metadata
- Added `end_profiling` method
- Added support for loading from IO objects
- Improved `input` and `output` for `seq` and `map` types

## 0.2.3 (2020-01-23)

- Updated ONNX Runtime to 1.1.1

## 0.2.2 (2019-12-24)

- Added support for session options
- Added support for run options
- Added `Datasets` module

## 0.2.1 (2019-12-19)

- Updated ONNX Runtime to 1.1.0

## 0.2.0 (2019-10-30)

- Added support for ONNX Runtime 1.0
- Dropped support for ONNX Runtime < 1.0

## 0.1.2 (2019-10-27)

- Added support for Numo::NArray
- Made thread-safe
- Fixed error with JRuby

## 0.1.1 (2019-09-03)

- Packaged ONNX Runtime with gem
- Added support for many more types
- Fixed output order with `output_names` option
- Fixed `File doesn't exist` on Windows

## 0.1.0 (2019-08-26)

- First release
