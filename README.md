# cbor-tests
The roundtrip and conformance tests for CBOR in Python

## The roundtrip test

The Kubernetes API objects are generated as JSON files in test_json directory. These fixtures are loaded as JSON objects into the test suite. The JSON objects go through the roundtrip of encoding into CBOR and decoding back to original object and ensure they remain the same.

## The conformance test

The conformance test runs a series of tests that decode CBOR hex string of various data types into its corresponding objects and then encode the objects back to the original hex string.

# How to run the test suite
```console
$ python -m pytest -vvv -s test/
```

# Test outputs
```console
test/test_conformance.py::test_integer[00-0] PASSED
test/test_conformance.py::test_integer[01-1] PASSED
test/test_conformance.py::test_integer[0a-10] PASSED
test/test_conformance.py::test_integer[17-23] PASSED
test/test_conformance.py::test_integer[1818-24] PASSED
test/test_conformance.py::test_integer[1819-25] PASSED
test/test_conformance.py::test_integer[1864-100] PASSED
test/test_conformance.py::test_integer[1903e8-1000] PASSED
test/test_conformance.py::test_integer[1a000f4240-1000000] PASSED
test/test_conformance.py::test_integer[1b000000e8d4a51000-1000000000000] PASSED
test/test_conformance.py::test_integer[1bffffffffffffffff-18446744073709551615] PASSED
test/test_conformance.py::test_integer[c249010000000000000000-18446744073709551616] PASSED
test/test_conformance.py::test_integer[3bffffffffffffffff--18446744073709551616] PASSED
test/test_conformance.py::test_integer[c349010000000000000000--18446744073709551617] PASSED
test/test_conformance.py::test_integer[20--1] PASSED
test/test_conformance.py::test_integer[29--10] PASSED
test/test_conformance.py::test_integer[3863--100] PASSED
test/test_conformance.py::test_integer[3903e7--1000] PASSED
test/test_conformance.py::test_float[f90000-0.0-fb0000000000000000] PASSED
test/test_conformance.py::test_float[f98000--0.0-fb8000000000000000] PASSED
test/test_conformance.py::test_float[f93c00-1.0-fb3ff0000000000000] PASSED
test/test_conformance.py::test_float[fb3ff199999999999a-1.1-fb3ff199999999999a] PASSED
test/test_conformance.py::test_float[f93e00-1.5-fb3ff8000000000000] PASSED
test/test_conformance.py::test_float[f97bff-65504.0-fb40effc0000000000] PASSED
test/test_conformance.py::test_float[fa47c35000-100000.0-fb40f86A0000000000] PASSED
test/test_conformance.py::test_float[fa7f7fffff-3.4028234663852886e+38-fb47efffffe0000000] PASSED
test/test_conformance.py::test_float[fb7e37e43c8800759c-1e+300-fb7e37e43c8800759c] PASSED
test/test_conformance.py::test_float[f90001-5.960464477539063e-08-fb3E70000000000000] PASSED
test/test_conformance.py::test_float[f90400-6.103515625e-05-fb3f10000000000000] PASSED
test/test_conformance.py::test_float[f9c400--4.0-fbc010000000000000] PASSED
test/test_conformance.py::test_float[fbc010666666666666--4.1-fbc010666666666666] PASSED
test/test_conformance.py::test_float[f97c00-inf-f97c00] PASSED
test/test_conformance.py::test_float[f9fc00--inf-f9fc00] PASSED
test/test_conformance.py::test_float[fa7f800000-inf-f97C00] PASSED
test/test_conformance.py::test_float[faff800000--inf-f9fc00] PASSED
test/test_conformance.py::test_float[fb7ff0000000000000-inf-f97C00] PASSED
test/test_conformance.py::test_float[fbfff0000000000000--inf-f9fc00] PASSED
test/test_conformance.py::test_float_nan[f97e00-nan] PASSED
test/test_conformance.py::test_special_values[f4-False] PASSED
test/test_conformance.py::test_special_values[f5-True] PASSED
test/test_conformance.py::test_special_values[f6-None] PASSED
test/test_conformance.py::test_special_values[f7-undefined] PASSED
test/test_conformance.py::test_string[60-] PASSED
test/test_conformance.py::test_string[6161-a] PASSED
test/test_conformance.py::test_string[6449455446-IETF] PASSED
test/test_conformance.py::test_string[62225c-"\\] PASSED
test/test_conformance.py::test_string[62c3bc-\xfc] PASSED
test/test_conformance.py::test_string[63e6b0b4-\u6c34] PASSED
test/test_conformance.py::test_invalid_integer_subtype PASSED
test/test_conformance.py::test_string_invalid_utf8[short] PASSED
test/test_conformance.py::test_string_invalid_utf8[long] PASSED
test/test_conformance.py::test_string_invalid_utf8[indefinite] PASSED
test/test_conformance.py::test_array[80-expected0] PASSED
test/test_conformance.py::test_array[83010203-expected1] PASSED
test/test_conformance.py::test_array[8301820203820405-expected2] PASSED
test/test_conformance.py::test_map[a0-expected0] PASSED
test/test_conformance.py::test_map[a201020304-expected1] PASSED
test/test_conformance.py::test_mixed_array_map[a26161016162820203-expected0] PASSED
test/test_conformance.py::test_mixed_array_map[826161a161626163-expected1] PASSED
test/test_conformance.py::test_mixed_array_map[a56161614161626142616361436164614461656145-expected2] PASSED
test/test_conformance.py::test_streaming[5f42010243030405ff-\x01\x02\x03\x04\x05-450102030405] PASSED
test/test_conformance.py::test_streaming[7f657374726561646d696e67ff-streaming-6973747265616d696e67] PASSED
test/test_conformance.py::test_streaming[9fff-decoded2-80] PASSED
test/test_conformance.py::test_streaming[9f018202039f0405ffff-decoded3-8301820203820405] PASSED
test/test_conformance.py::test_streaming[9f01820203820405ff-decoded4-8301820203820405] PASSED
test/test_conformance.py::test_streaming[83018202039f0405ff-decoded5-8301820203820405] PASSED
test/test_conformance.py::test_streaming[83019f0203ff820405-decoded6-8301820203820405] PASSED
test/test_conformance.py::test_streaming[9f0102030405060708090a0b0c0d0e0f101112131415161718181819ff-decoded7-98190102030405060708090a0b0c0d0e0f101112131415161718181819] PASSED
test/test_conformance.py::test_streaming[bf61610161629f0203ffff-decoded8-a26161016162820203] PASSED
test/test_conformance.py::test_streaming[826161bf61626163ff-decoded9-826161a161626163] PASSED
test/test_conformance.py::test_streaming[bf6346756ef563416d7421ff-decoded10-a26346756ef563416d7421] PASSED
test/test_conformance.py::test_streaming[d901029f010203ff-decoded11-d9010283010203] PASSED
test/test_conformance.py::test_datetime[c074323031332d30332d32315432303a30343a30305a-False-expected0] PASSED
test/test_conformance.py::test_datetime[c0781b323031332d30332d32315432303a30343a30302e3338303834315a-False-expected1] PASSED
test/test_conformance.py::test_datetime[c07819323031332d30332d32315432323a30343a30302b30323a3030-False-expected2] PASSED
test/test_conformance.py::test_datetime[c11a514b67b0-True-expected3] PASSED
test/test_conformance.py::test_datetime[c1fb41d452d9ec07e6b4-True-expected4] PASSED
test/test_conformance.py::test_datetime[c11a514b67b0-True-expected5] PASSED
test/test_conformance.py::test_positive_bignum[c249010000000000000000-18446744073709551616] PASSED
test/test_conformance.py::test_negative_bignum[c349010000000000000000--18446744073709551617] PASSED
test/test_conformance.py::test_indefinite_overflow[string] PASSED
test/test_conformance.py::test_indefinite_overflow[bytes] PASSED
test/test_roundtrip.py::test_json PASSED
```
